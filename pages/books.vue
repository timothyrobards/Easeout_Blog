<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(75vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
      <div class="item xs-block xs-full-height">
        <h1 class="xs-py3 main-title">Books 📚</h1>
        <div class="book-grid">

          <article class="card">
            <header class="card__thumb">
              <img src="https://www.easeout.co/images/uploads/the-css-guide-wide.png" alt="CSS book cover" />
            </header>
            <!-- <div class="card__price">
              <span class="card__price__current">$15</span>
              <br/>
              <span class="card__price__secondary">$25</span>
            </div> -->
  
            <div class="card__body">
              <div class="card__category card__category__css"><a href="/books/the-css-guide">CSS</a></div>
              <h2 class="card__title"><a href="/books/the-css-guide">The CSS Guide</a></h2>
              <div class="card__subtitle">The Complete Guide to Modern CSS.</div>
              <p class="card__description">Whether you're new to web development or a more seasoned developer looking to refine your skills. The CSS Guide will take you from beginner to expert! &nbsp;<a class="read-more" href="/books/the-css-guide">Read More</a></p>
            </div>
  
            <footer class="card__footer">
              <span class="icon"></span> Updated December 2020
            </footer>
          </article>

          <article class="card">
            <header class="card__thumb">
              <img src="https://www.easeout.co/images/uploads/getting-sassy-wide.png" alt="SASS book cover" />
            </header>
            <!-- <div class="card__price">
              <span class="card__price__current">$15</span>
              <br/>
              <span class="card__price__secondary">$25</span>
            </div> -->
  
            <div class="card__body">
              <div class="card__category card__category__sass"><a href="/books/getting-sassy">SASS</a></div>
              <h2 class="card__title"><a href="/books/getting-sassy">Getting SASSY: A Practical Guide</a></h2>
              <div class="card__subtitle">A Practical Guide to SASS.</div>
              <p class="card__description">Are you ready to take your web development skills to the next level? It's time to GET SASSY! Learn how to create faster, leaner, more maintainable code! &nbsp;<a class="read-more" href="/books/getting-sassy">Read More</a></p>
            </div>
  
            <footer class="card__footer">
              <span class="icon"></span> Updated February 2021
            </footer>
          </article>

          <article class="card">
            <header class="card__thumb">
              <img src="https://www.easeout.co/images/uploads/coming-soon.jpg" alt="JavaScript book cover" />
            </header>
            <!-- <div class="card__price">
              <span class="card__price__current">$15</span>
              <br/>
              <span class="card__price__secondary">$25</span>
            </div> -->
  
            <div class="card__body">
              <div class="card__category card__category__javascript"><a href="#">JavaScript</a></div>
              <h2 class="card__title"><a href="#">Mastering JavaScript</a></h2>
              <div class="card__subtitle">The Complete Guide to JavaScript Mastery.</div>
              <p class="card__description">Available Summer 2021 <br> <a class="read-more" href="https://easeout.eo.page/news">Sign up to be notified!</a></p>
            </div>
  
            <footer class="card__footer">
              <span class="icon"></span> Coming Soon!
            </footer>
          </article>
        </div>
      </div>
      </div>
    </div>
  </main>
</template>

<script>
import BaelGrid from '~/components/BaelGrid'
export default {
    watchQuery: ['page'],

   async asyncData({ params, app, payload, route, store }) {
 
    await store.commit("SET_TITLE", "Books");

  
  },
     transition (to, from) {
    if (!from) return 'fade'
    return +to.query.page > +from.query.page ? 'slide-right' : 'slide-left'
  },
  components: {BaelGrid},
  data() {
    return {};
  },
    head() {
    return {
      title: "Easeout Books | " + this.$store.state.siteInfo.sitename,
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'Our collection of guidebooks about coding & design.'
      }],
    };
  },
  data() {
    return {};
  },
  methods: {
    onResize(event) {
      this.navHeight();
      console.log(this.$store.state.navheight);
      console.log("slug resize");
    },
    navHeight() {
      var height = document.getElementById("navbar").clientHeight;
      this.$store.commit("SET_NAVHEIGHT", height);
    }
  },
  updated() {
    if (process.browser) {
      this.$nextTick(() => {
           this.$store.commit("paginateOff", false);

        this.navHeight();
        console.log(this.$store.state.navheight);
        console.log("slug updated");
      });
    }
  },
  mounted() {
    if (process.browser) {
      this.$nextTick(() => {
        this.navHeight();
                   this.$store.commit("paginateOff", false);

        window.addEventListener("resize", this.onResize);
        console.log(this.$store.state.navheight);
        console.log("slug mounted");
      });
    }
  },
  beforeDestroy() {
    // Unregister the event listener before destroying this Vue instance
    window.removeEventListener("resize", this.onResize);
  },

  computed: {
    allBlogPosts() {
      return this.$store.state.blogPosts;
    },
    navbarheight() {
      return this.$store.state.navheight;
    }
  }
};
</script>

<style scoped>

.book-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
  justify-items: center;
  padding-top: 2em;
}

@media only screen and (max-width: 1000px) {
  .book-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media only screen and (max-width: 600px) {
  .book-grid {
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
  margin-bottom: 4em;
}
.card a {
  color: inherit;
  text-decoration: none;
}

.card:hover {
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.3);
}

/**
* DATE
**/
.card__price {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 45px;
  height: 45px;
  padding-top: 10px;
  background-color: orange;
  border-radius: 50%;
  color: #fff;
  text-align: center;
  font-weight: 700;
  line-height: 13px;
}
.card__price__current {
  font-size: 14px;
}
.card__price__secondary {
  text-transform: uppercase;
  text-decoration: line-through;
  font-size: 10px;
}

/**
* THUMB
**/
.card__thumb {
  height: 245px;
  overflow: hidden;
  background-color: #000;
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
  /* object-position: 0px -70px; */
}
.card:hover .card__thumb {
  height: 130px;
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
  height: 150px;
  padding: 20px;
  -webkit-transition: height 0.5s;
  transition: height 0.5s;
}
.card:hover .card__body {
  height: 260px;
}

@media only screen and (max-width: 1024px) {
  .card__body {
    height: 150px !important;
  }
  
  .card__description {
    position: static !important;
  }
  
  .card:hover .card__body {
    height: 270px !important;
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
    height: 140px !important;
  }

  .card:hover .card__body {
    height: 250px !important;
  }
}

@media only screen and (max-width: 360px) {  
  .card__body {
    height: 150px !important;
  }

  .card:hover .card__body {
    height: 290px !important;
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
  top: 120px;
  left: 20px;
  right: 20px;
  bottom: 56px;
  margin: 0;
  padding: 0;
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

</style>