<template>
  
<div class="xs-text-6 md-text-5 main">

  

  <div v-if="$route.fullPath==='/'">
    <div class="landing" :style="`margin-top:${navbarheight}px; margin-bottom: -${navbarheight}px;`">

      <div class="blog-grid">
  <div class="div-article">
      

      <div class="diagonal-box">
        <div class="content" style="font-size:1em;">
          <h1 class="intro">
            Ready to <span class="outline">level up</span> your freelance skills?🚀
            <!-- <span class="outline">Launch</span> <span class="redline"></span> your freelancing business! 🚀 -->
          </h1>
          <br><br>
         
          <p style="margin-top:30px" class= "xs-text-4">Hey, I'm Tim &#128075;</p>
          <br><p class= "xs-text-4">I launched EASEOUT in 2019 with a mission to share what I’ve learned over my years working in web development. Over time I've built up a solid resource for anyone interested in learning about building websites!</p>
          <!-- <br><p>I’ve built several courses on topics such as CSS, SASS and JavaScript. And you’ll find a lot of my tutorials on this website! Or you can checkout my web dev <a href="https://www.easeout.co/books/">guidebooks</a> if you’d like.</p> -->
          <br><p class= "xs-text-4">Fast forward to the present, and I am now focusing my energy into my other passion.. freelancing! I have run my own freelance business for years and I believe I have a lot of knowledge to benefit new and experienced freelancers alike.</p>
          <br><p class= "xs-text-4">I know the initial pain of finding it hard to get new clients and earn a consistent income. So thats why I’ve introduced my solution, the <a href="/freelance/">Complete Guide to Freelancing</a>.</p>
          <!-- <br><div>
            <img src="https://www.easeout.co/images/uploads/javascript-mastery-mockup.jpg" class="freelance-main-image" alt="Mastering JavaScript cover mockup" />
          </div> -->
          <br><p class= "xs-text-4">Freelancing has opened up a world of opportunities for me, and I’m certain it can do the same for you!</p>
          <br><p class= "xs-text-4">While you're here, check out my blog where I post freelancing tips, code tutorials, design inspiration, useful resources, and much more! You can also <a href="https://easeout.eo.page/news">join the newsletter</a>, or find me on <a href="https://twitter.com/easeoutco">Twitter/X</a>.</p>    
          <br><p class= "xs-text-4">Thanks for stopping by!</p>       
          <br><div>
            <img src="~/assets/timprofile.jpeg" class="profile-main-image" alt="Tim profile image" />
          </div>
        </div>
        <h2 class="blog-title">Latest from the blog:</h2>
      </div>
    </div>
  </div>
    <div v-if="items2[0]" class="full-height single" :style="`margin-top:${navbarheight}px;`">
      <div class="card-grid">
      <div v-if="items2[pi]" v-for="(p,pi) in items2" :key="p.pi">  

        <article class="card">

        <div v-if="p.thumbnail" class="">

           <nuxt-link :to="p._path">
              <header class="card__thumb">
              <img  v-lazy="p.thumbnail" :key="p.thumbnail">
              </header>
              <div v-if="!p.thumbnail" class="full-bg-color"></div>
            </nuxt-link>
           
           <div>
            
            <div class="card__body">
            <nuxt-link class="full-bg-link" :to="p._path">
              <h2 class="card__title">{{p.title}}</h2> 
              <p class="card__subtitle">{{p.short}}</p>
              <p class="card__description">
                {{p.body | truncate(150, '...') | striphtml | stripmarkdown }}
                <nuxt-link class="read-more" :to="p._path">Read more ➡️</nuxt-link>
              </p>
              <footer class="card__footer">{{p.dateshort}}</footer>
            </nuxt-link>
            </div>

            <nuxt-link v-if="p.category === 'Inspiration'" class="tag tag-pos tag-inspo tag__link text-white" :to="`/category/inspiration/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'Template'" class="tag tag-pos tag-template tag__link text-white" :to="`/category/template/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'Article'" class="tag tag-pos tag-article tag__link text-white" :to="`/category/article/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'React'" class="tag tag-pos tag-react tag__link text-black" :to="`/category/react/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'JavaScript'" class="tag tag-pos tag-javascript tag__link text-black" :to="`/category/javascript/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'CSS'" class="tag tag-pos tag-css tag__link text-black" :to="`/category/css/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'HTML'" class="tag tag-pos tag-html tag__link text-white" :to="`/category/html/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'SASS'" class="tag tag-pos tag-sass tag__link text-white" :to="`/category/sass/`">
             {{p.category}}
            </nuxt-link>

            <nuxt-link v-if="p.category === 'GIT'" class="tag tag-pos tag-git tag__link text-white" :to="`/category/git/`">
             {{p.category}}
            </nuxt-link>

           </div>

        </div>
        <div v-else>

        <nuxt-link  :to="p._path">
              <header class="card__thumb">
              <img src="https://www.easeout.co/images/uploads/grid.png">
              </header>
              <div v-if="!p.thumbnail" class="full-bg-color"></div>
            </nuxt-link>
            
            <div class="card__body">
            <nuxt-link class="full-bg-link" :to="p._path">
              <h2 class="card__title">{{p.title}}</h2> 
              <p class="card__subtitle">{{p.short}}</p>
              <p class="card__description">
                {{p.body | truncate(150, '...') | striphtml | stripmarkdown }}
                <nuxt-link class="read-more" :to="p._path">Read more ➡️</nuxt-link>
              </p>
              <footer class="card__footer">{{p.dateshort}}</footer>
            </nuxt-link>
            </div>

          <nuxt-link v-if="p.category === 'CSS'" class="tag tag-pos tag-css tag__link text-black" :to="`/category/css/`">
          {{p.category}}
          </nuxt-link>

          <nuxt-link v-if="p.category === 'SASS'" class="tag tag-pos tag-sass tag__link text-white" :to="`/category/sass/`">
          {{p.category}}
          </nuxt-link>

          <nuxt-link v-if="p.category === 'HTML'" class="tag tag-pos tag-html tag__link text-white" :to="`/category/html/`">
          {{p.category}}
          </nuxt-link>

          <nuxt-link v-if="p.category === 'GIT'" class="tag tag-pos tag-git tag__link text-white" :to="`/category/git/`">
          {{p.category}}
          </nuxt-link>

          <nuxt-link v-if="p.category === 'React'" class="tag tag-pos tag-react tag__link text-black" :to="`/category/react/`">
          {{p.category}}
          </nuxt-link>

          <nuxt-link v-if="p.category === 'JavaScript'" class="tag tag-pos tag-javascript tag__link text-black" :to="`/category/javascript/`">
          {{p.category}}
          </nuxt-link>
          
        </nuxt-link>
    
        </div>
        </article>
      </div>
      </div>

    </div>


    <div v-else class="r full-height browse">
      <div class="xs-p2 c-100 xs-flex xs-flex-align-center xs-flex-justify-center xs-text-center" :style="`height:calc(100vh - ${navbarheight}px);margin-top:${navbarheight}px`">

        
        <div v-if="total < 1 && !busy">No Results.</div>
      </div>

  </div>
  </div>
  </div>

  <div class="div-ads"> 
              <br />
              <!-- My eBook-->
              <a href="https://easeout.gumroad.com/l/freelance" target="_blank"><img src="https://www.easeout.co/_nuxt/img/77e5652.svg" class="center" alt="The Complete Guide to Freelancing"/>
              </a><br /><br />
              <!-- Notion-->
              <a href="https://affiliate.notion.so/zwb1vda2tuk0" target="_blank">
                <img src="~/assets/notion-banner.png" class="center" alt="Notion ad"/>
              </a><br /><br />
              <!-- Bonsai-->
              <a href="https://www.hellobonsai.com/?fp_ref=easeout" target="_blank" style="outline:none;"><img src="https://d2gdx5nv84sdx2.cloudfront.net/uploads/zjdg88yr/marketing_asset/banner/10354/Bonsai_All-in-one_software_for_Freelancers.png" class="center" alt="hellobonsai"/>
              </a><br /><br />
              <!-- Remote.io-->
              <a href="https://go.remote.io/partner.php?id=320" target="_blank"><img src="https://go.remote.io/media/banners/300x250_manwithphone_V1.png" class="center" alt="Recruiting remote talent?">
              </a><br /><br />
              <!-- Botsonic-->
              <a href="https://writesonic.com/botsonic?fpr=tim85" target="_blank">
                <img src="~/assets/Ad 6.jpg" class="center" alt="Botsonic ad"/>
              </a><br /><br />
              <!-- Educative-->
              <a href="https://www.educative.io/unlimited?aff=KNqG" target="_blank">
                <img src="~/assets/educative-banner-ad.png" class="center" alt="Educative Inc"/>
              </a><br />
              <!-- Sponsor CTA -->
              <small class="center"> Want your ad here? <a href="mailto:hello@easeout.co">Contact us!</a></small>
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
      if (this.allitems.length > 9) {
        this.$store.commit("paginateOn", true);
        this.$store.commit("resultsLength", this.allitems.length);
      } else if (this.allitems.length < 9) {
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
          for (var i = 0, j = 9; i < j; i++) {
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
        return Number(this.queryParam - 1) * 9;
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

  filters: {
        truncate: function (text, length, suffix) {
            if (text.length > length) {
                return text.substring(0, length) + suffix;
            } else {
                return text;
            }
        },
        striphtml: function (string) {
            return string.replace(/<\/?[^>]+>/ig, " "); 
        },
        stripmarkdown: function (string) {
            return string.replace(/(__|\*|\#)/gm, '');
        },
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
  background-color: #fff;
  /* background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Cg fill-rule='evenodd'%3E%3Cg fill='%23006dff' fill-opacity='0.4'%3E%3Cpath opacity='.5' d='M96 95h4v1h-4v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9zm-1 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9z'/%3E%3Cpath d='M6 5V0H5v5H0v1h5v94h1V6h94V5H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E"); */
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
    /* --width: 64rem; */
    --width: 75%;
  }
}

@media (max-width: 15em) {
  :root {
    --width: 90%;
  }
}

.diagonal-box {
  position: relative;
  /* padding: var(--skew-padding) 0; */
  padding: 3em 0 1em 0;
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
  background: #FFE800;
  color: #003;
  font-weight: 900;
  padding: 0.5em;
  text-transform: uppercase;
  border: 1px solid slategrey;
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
  /* -webkit-text-stroke-width: 0.05em; */
  -webkit-text-fill-color: #B206FF;
}

.redline {
  border-bottom: 4px solid red;
  transition: none;
}

/* .intro-links {
  margin: 2.5em auto 0em;
  text-align: center;
  font-size: 1em;
  background: transparent;
  text-transform: uppercase;
}

.intro-links a {
  color: #000;
}

@media (max-width: 1024px) {
  .intro-links, .c-6.center {
    display: none;
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
ul.list-horizontal li { display: inline-block; } */

.full-height-css{
  background-color: yellow !important;
}

.blog-title {
  padding-bottom: 20px;
  text-align: center;
}

/* TAG STYLES */
  .tag-css {
    background-color: #95DEE3;
    border-color: #95DEE3;
  }

  .tag-sass {
    background-color: #CF679A;
    border-color: #CF679A;
  }

  .tag-html {
    background-color: #EA6228;
    border-color: #EA6228;
  }

  .tag-git  {
    background-color: #E94D31;
    border-color: #E94D31;
  }

  .tag-react {
    background-color: #00D8FF;
    border-color: #00D8FF;
  }

  .tag-javascript {
    background-color: #EFD81D;
    border-color: #EFD81D;
  }

  .tag-article {
    background-color: #174528;
    border-color: #174528;
  }
  
  .tag-inspo {
    background-color: #F7786B;
    border-color: #F7786B;
  }

  .tag-news {
    background-color: #5B5EA6;
    border-color: #5B5EA6;
  }

  .tag-books {
    background-color: #282C34;
    border-color: #282C34;
  }

  .tag-template {
    background-color: #00A591;
    border-color: #00A591;
  }

  .text-black {
    color: #282C34;
  }

  /* TAG OVERRIDE DEFAULTS */
  
  .tag {
    z-index: 2;
    margin-top: 5px;
    font-size: 0.85rem;
    line-height: 1.5rem;
    letter-spacing: 1px;
  }

  .tag__link {
    padding: 0 .5rem;
  }

/**
* CARD GRID
**/

.card-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
  justify-items: center;
  padding-top: 2em;
  padding: 20px;
}

@media only screen and (max-width: 950px) {
  .card-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media only screen and (max-width: 600px) {
  .card-grid {
    grid-template-columns: 1fr;
  }
}
/**
* BOOK CARD
**/
.card {
  position: relative;
  background-color: #fff;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  -webkit-transition: box-shadow 0.5s;
  transition: box-shadow 0.5s;
  margin-bottom: 1em;
}
.card a {
  color: inherit;
  text-decoration: none;
}

.card:hover {
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.3);
}

/**
* THUMB
**/
.card__thumb {
  height: 250px;
  overflow: hidden;
  background-color: #fff;
  -webkit-transition: height 0.5s;
  transition: height 0.5s;
  object-fit: cover;
}
.card__thumb img {
  display: block;
  opacity: 1;
  -webkit-transform: scale(1);
          transform: scale(1);
  -webkit-transition: opacity 0.5s, -webkit-transform 0.5s;
  transition: opacity 0.5s, -webkit-transform 0.5s;
  transition: opacity 0.5s, transform 0.5s;
  transition: opacity 0.5s, transform 0.5s, -webkit-transform 0.5s;
}

.card__thumb__centered {
  display: none;
}
.card:hover .card__thumb {
  height: 140px;
}

.card:hover .card__thumb img {
  opacity: 0.6;
  -webkit-transform: scale(1.2);
          transform: scale(1.2);
}

@media only screen and (max-width: 1000px) {
  .card__thumb img {
    object-position: 0px 0px;
  }
}

/**
* BODY
**/
.card__body {
  position: relative;
  height: 190px;
  padding: 0px 20px 0px 20px;
  -webkit-transition: height 0.5s;
  transition: height 0.5s;
}
.card:hover .card__body {
  height: 300px;
}

@media only screen and (max-width: 1024px) {
  .card__body {
    height: 120px;
  }
  .card:hover .card__body {
    height: 120px !important;
  }

  .card__thumb {
    height: 300px;
  }
  .card:hover .card__thumb {
    height: 300px;
  }
  
  .card__description {
    display: none;
  }

  .card__subtitle {
    display: none;
  }

  .card:hover .card__thumb img {
    opacity: 0.6;
    -webkit-transform: scale(1.2);
          transform: scale(1.2);
    }
}

/* @media only screen and (max-width: 800px) {
  .card__body {
    height: 150px !important;
  }
  
  .card:hover .card__body {
    height: 240px !important;
  }
} */

@media only screen and (max-width: 600px) {  
  .card__body {
    height: 17vh;
  }
  .card:hover .card__body {
    height: 17vh !important;
  }

  .card__thumb {
    height: 38vh;
  }
  .card:hover .card__thumb {
    height: 38vh;
  }

  .card:hover .card__thumb img {
    opacity: 0.6;
    -webkit-transform: scale(1);
          transform: scale(1);
  }

  .card__thumb img{
    /* object-position: 0px -4vh; */
  }
}

@media only screen and (max-width: 360px) {  
  .card__thumb img{
    /* object-position: 0px -4vh; */
  }
}

.card__category {
  position: absolute;
  top: -25px;
  left: 0;
  height: 25px;
  padding: 0 15px;
  color: #fff;
  text-transform: uppercase;
  font-size: 11px;
  line-height: 25px;
}

.card__category__css {
  background-color: #95DEE3;
  color: #000;
}

.card__category__sass {
  background-color:#CF679A;
}

.card__category__javascript {
  background-color:#EFD81D;
  color: #000;
}

.card__title {
  margin: 0;
  padding: 0 0 10px 0;
  color: #000;
  font-size: 22px;
  font-weight: bold;
  text-transform: uppercase;
}

.card__subtitle {
  margin: 0;
  padding: 0 0 10px 0;
  font-size: 19px;
}

.card__description {
  position: absolute;
  /* top: 120px;
  left: 20px;
  right: 20px;
  bottom: 56px; */
  margin: 0;
  padding: 0 20px 0 0;
  color: #666C74;
  font-size: 14px;
  line-height: 25px;
  opacity: 0;
  -webkit-transform: translateY(45px);
          transform: translateY(45px);
  -webkit-transition: opacity 0.3s, -webkit-transform 0.3s;
  transition: opacity 0.3s, -webkit-transform 0.3s;
  transition: opacity 0.3s, transform 0.3s;
  transition: opacity 0.3s, transform 0.3s, -webkit-transform 0.3s;
  -webkit-transition-delay: 0s;
          transition-delay: 0s;
}

@media only screen and (max-width: 800px) {
  .card__description {
    position: static;
  }
}

.card:hover .card__description {
  opacity: 1;
  -webkit-transform: translateY(0);
          transform: translateY(0);
  -webkit-transition-delay: 0.2s;
          transition-delay: 0.2s;
}

.card__footer {
  position: absolute;
  bottom: 12px;
  /* left: 20px; */
  right: 20px;
  font-size: 11px;
  color: #A3A9A2;
}

.icon {
  display: inline-block;
  vertical-align: middle;
  margin: -2px 0 0 2px;
  font-size: 18px;
}
.icon + .icon {
  padding-left: 10px;
}

.read-more {
  color: #0F65EF !important;
}

.read-more:hover {
  opacity: .8;
}
.freelance-main-image{
  display: block;
  margin-left: auto;
  margin-right: auto;
  /* width: 50%; */
  height: 200px;
}
.profile-main-image{
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}
.profile-main-image-landing{
  display: block;
  /* margin-left: auto;
  margin-right: auto; */
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  float:left;
}
.authorbox{
  border: 5px purple dashed;
  background:#282C34;
  color: white;
  padding: 1em;
}

.authorbox p {
  float:right; 
  width:80%;
}

.authorbox:after {
  content: "";
  display: table;
  clear: both;
}

@media only screen and (max-width: 1024px) {
  .authorbox p { 
    width:75%;
  }
}

@media only screen and (max-width: 800px) {
  .profile-main-image-landing{
    width: 90px;
    height: 90px;
    margin-left:2%;
  }
  
  .authorbox p {
    float:right; 
    width:77%;
  }
}

@media only screen and (max-width: 650px) {
  .profile-main-image-landing{
    float:none;
    margin-left: auto;
    margin-right: auto;
  }
  .authorbox p {
    float:none; 
    padding-top:1em;
    width:100%;
  }
}
</style>
