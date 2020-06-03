<template>
<div class="xs-text-6 md-text-5 main">

  <div v-if="$route.fullPath==='/'">
    <div class="landing" :style="`margin-top:${navbarheight}px; margin-bottom: -${navbarheight}px;`">
      <div class="diagonal-box">
        <div class="content">
          <h1 class="intro">
            <span class="outline">Design & code</span> tutorials to <span class="redline">boost</span> your web development skills. 💻 🌈
          </h1>
          <br>
          <ul class="intro-links list-horizontal">
            <li>💻 <nuxt-link to="/category/article/" exact>Articles</nuxt-link></li>
            <li>📘 <nuxt-link to="/category/css/" exact>CSS</nuxt-link></li>
            <li>❤️ <nuxt-link to="/category/inspiration/" exact>Inspiration</nuxt-link></li>
            <li>📰 <nuxt-link to="/category/newsletter/" exact>News</nuxt-link></li>
            <li>🏁 <nuxt-link to="/category/template/" exact>Templates</nuxt-link></li>
          </ul>
        </div>
      </div>
    </div>
  </div>

    <div v-if="items2[0]" class="r browse full-height" :style="`margin-top:${navbarheight}px;`">
      <div v-if="items2[pi]" v-for="(p,pi) in items2" :key="p.pi" class="xs-p2 full-item">  

        <div v-if="p.thumbnail" class="item xs-block xs-full-height xs-flex xs-relative xs-flex-align-start xs-flex-justify-end xs-text-left">
           
           <div class="xs-text-left xs-flex xs-full-height xs-flex-justify-end xs-flex-align-end xs-width-auto">

            <nuxt-link class="full-bg-link" :to="p._path">
             {{p.title}} <span class="card-date">/ {{p.dateshort}}</span>
            </nuxt-link>

            <nuxt-link v-if="p.category === 'Inspiration'" class="tag tag-pos tag-inspo tag__link text-white" :to="`/category/inspiration/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'Template'" class="tag tag-pos tag-template tag__link text-white" :to="`/category/template/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'Article'" class="tag tag-pos tag-article tag__link text-white" :to="`/category/article/`">
             {{p.category}}
            </nuxt-link>

           </div>

            <nuxt-link  :to="p._path">
              <img  v-lazy="p.thumbnail" :key="p.thumbnail" class="full-bg-image">
              <div v-if="!p.thumbnail" class="full-bg-color"></div>
            </nuxt-link>

        </div>
        <div v-else class="item item-txt xs-block xs-full-height xs-flex xs-relative xs-flex-align-center xs-flex-justify-center xs-text-center">
        
        <nuxt-link class="nobg-link" :to="p._path">
          {{p.title}}
          <div class="item-txt-secondary"> {{p.description}} </div>

          <nuxt-link v-if="p.category === 'CSS'" class="tag tag-pos tag-css tag__link text-black" :to="`/category/css/`">
          {{p.category}}
          </nuxt-link>
        </nuxt-link>
        

    
        </div>
      </div>

    </div>
    <div v-else class="r full-height browse">
      <div class="xs-p2 c-100 xs-flex xs-flex-align-center xs-flex-justify-center xs-text-center" :style="`height:calc(100vh - ${navbarheight}px);margin-top:${navbarheight}px`">

        
        <div v-if="total < 1 && !busy">No Results.</div>
      </div>

  </div>
  </div>
</template>

<script>

export default {
  props: ["items", "allitems"],
  data() {
    return {
      currentPage: null,
      pageNumbers: [],
      pageNumberCount: 0,
      items2: [],
      query: 1,
      busy: false,
      count: 0
    };
  },
  methods: {
    pageCheck() {
      if (this.allitems.length > 12) {
        this.$store.commit("paginateOn", true);
        this.$store.commit("resultsLength", this.allitems.length);
      } else if (this.allitems.length < 12) {
        this.$store.commit("paginateOff", false);
      } else {
        this.$store.commit("paginateOff", false);
      }
    },

    loadMore() {
      this.count = this.offset;
      if (this.total > this.count && this.busy == false) {
        this.busy = true;

     
          this.items2.splice(0);
          for (var i = 0, j = 12; i < j; i++) {
            let api = this.allitems[this.count];

            this.items2.push(api);
            this.count++;
          }

          this.busy = false;
        
      }
    },

    onResize(event) {
      this.navHeight();
    },

    navHeight() {
      if (process.browser) {
        var height = document.getElementById("navbar").clientHeight;

        this.$store.commit("SET_NAVHEIGHT", height - 1);
      }
    }
  },
  watch: {
    // whenever question changes, this function will run
    $route({ params, query }) {
      if (this.$route.query.page > 1) {
        this.loadMore();
        this.navHeight();
        this.pageCheck();
      } else if (this.$route.query.page == null) {
        this.$route.query.page = 1;
        this.loadMore();
          this.navHeight();
        this.pageCheck();
      } else {
        this.loadMore();
          this.navHeight();
        this.pageCheck();
      }
    },
    queryParam: function() {
      this.loadMore();
    }
  },
  computed: {

    offset() {
      if (this.queryParam > 1) {
        return Number(this.queryParam - 1) * 12;
      } else {
        return 0;
      }
    },
    prevpage() {
      var prev = Number(this.queryParam) - 1;
      return prev;
    },
    nextpage() {
      var next = Number(this.queryParam) + 1;
      return next;
    },
    navbarheight() {
      return this.$store.state.navheight;
    },
    total() {
      return this.allitems.length;
    },

    queryParam() {
      if (this.$route.query.page == null) {
        return 1;
      } else {
        return Number(this.$route.query.page);
      }
    }
  },

  updated() {
    this.$nextTick(() => {
      this.pageCheck();
      this.navHeight();
      this.$store.commit("SET_GRIDOFFSET", this.offset);
    });
  },
  mounted() {
    if (process.browser) {
      this.loadMore();

      this.$nextTick(() => {
        this.navHeight();
        this.pageCheck();
        window.addEventListener("resize", this.onResize);
      });
    }
  },
  beforeDestroy() {
    // Unregister the event listener before destroying this Vue instance
    window.removeEventListener("resize", this.onResize);
  }
};
</script>

<style>
img[lazy='loading'] {opacity:0;transition: .8s all;transition-delay:.8s;}
img[lazy='loaded'] {opacity:1;transition: .8s all;transition-delay:.8s;}
.nobg-link {font-size: calc(1rem + 1vw); color: #dfa612; line-height: 36px; padding: 0 0.5rem 0 0.5rem;}
@media (max-width: 640px) {
  .nobg-link {
    font-size: calc(1rem + 5vw);
    line-height: 46px;
  }
}
.nobg-link:hover {color: #dfa612; opacity:.8;transition: .4s all;}
.full-bg-link {z-index:2;padding:1.2rem;transition: .8s all;}
.item-txt {border: 1px solid rgba(0,0,0,.2); background:#282C34;
background: radial-gradient(circle, #282C34 19%, #282C34 100%); font-family: 'Overpass Mono', monospace;}
.item-txt-secondary {font-size: 1rem; line-height: 26px; padding: 1.5rem 0.5rem 0 0.5rem; font-family: 'Overpass Mono', monospace; color: #faebd7;}
@media (max-width: 640px) {
  .item-txt-secondary {
    padding: 2.5rem 0.5rem 0 0.5rem;
  }
}
.full-bg-image {position:absolute;top:0;left:0;right:0;bottom:0;object-fit:cover;object-position:center top;width:100%;height:100%;transition: .4s all;border: 1px solid rgba(0,0,0,.2);}
.item:hover .full-bg-image,.item:hover .full-bg-color  {filter: brightness(120%);transition: .4s all;}
.item .full-bg-link  {background: #fff;transition: .8s all;border-top: 1px solid rgba(0,0,0,.2);border-right: 1px solid rgba(0,0,0,.2);}
.full-bg-link h2 {margin:0;}
.tag-pos {
  position:absolute;top:0.5rem;right:0.5rem;width:unset!important;transition: .8s all;
}
.card-date{
  color: grey;
  font-size: 0.75rem;
}

/* ==============================
LANDING HERO STYLES
================================*/

.main {
  background-color: #f9f9f9;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Cg fill-rule='evenodd'%3E%3Cg fill='%23006dff' fill-opacity='0.4'%3E%3Cpath opacity='.5' d='M96 95h4v1h-4v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9zm-1 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9z'/%3E%3Cpath d='M6 5V0H5v5H0v1h5v94h1V6h94V5H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
}

:root {
  --width: 100vw;
  --full-width: 100vw;
  --angle: -5deg;
  /*-----------------
  Magic Number Alert:
  
  the 0.09719 is calculated by this formula:
  tan(11°) / 2
  11° is the current skewY value.
  ------------------*/
  --magic-number: 0.09719;
  --skew-padding: calc(var(--width) * var(--magic-number));
  --clip-padding: calc(var(--full-width) * var(--magic-number));
}
@media (min-width: 42em) {
  :root {
    --width: 64rem;
  }
}

.diagonal-box {
  position: relative;
  /* padding: var(--skew-padding) 0; */
  padding: 4em 0 1em 0;
  margin-top: -1px;
}

@media (max-width: 640px) {
  .diagonal-box {
    padding: 3em 0 0 0;
  }
}
.diagonal-box:before {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  transform: skewy(var(--angle));
  transform-origin: 50% 0;
  outline: 1px solid transparent;
  backface-visibility: hidden;
}

.content {
  max-width: var(--width);
  margin: 0 auto;
  padding: 1.5em;
  position: relative;
}

/* --------------------
Landing Presentational Styles 
-------------------- */
*, *:before, *:after {
  box-sizing: border-box;
}

@media (min-width: 70em) {
  .landing {
    font-size: 125%;
  }
}

.intro {
  font-size: 2.5em;
  transform: skewY(var(--angle));
  margin: 0em auto 0em;
  text-align: center;
  background: #FFFF00;
  color: #003;
  font-weight: 900;
  padding: 0.5em;
  text-transform: uppercase;
  border: 1px solid black;
}

@media (max-width: 640px) {
  .intro {
    font-size: 2.3em;
  }
}

.outline {
  color: #fff;
  text-transform: uppercase;
  font-weight: 900;
  letter-spacing: 2px;
  -webkit-text-stroke-color: #000;
  -webkit-text-stroke-width: 0.05em;
  -webkit-text-fill-color: #fff;
}

.redline {
  border-bottom: 4px solid red;
  transition: none;
}

.intro-links {
  margin: 2.5em auto 0em;
  text-align: center;
  font-size: 1.2em;
  background: transparent;
  text-transform: uppercase;
}

.intro-links a {
  color: #000;
}

@media (max-width: 640px) {
  .intro-links {
    font-size: 1.3em;
    line-height: 1.5;
  }
}

.intro-links a:hover {
  color: darkslategrey;
}

.intro-links li {
  padding-left: .25em;
}

.intro-links:first-of-type {
  padding-left: 0em;
}

ul.list-horizontal { text-align: center;}
ul.list-horizontal li { display: inline-block; }

.full-height-css{
  background-color: yellow !important;
}

</style>
