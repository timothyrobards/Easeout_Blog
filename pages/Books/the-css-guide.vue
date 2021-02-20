<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(75vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
      <div class="item xs-block xs-full-height">
        <div class="book-grid">
          <div>
              <h1 class="xs-py3 main-title">The CSS Guide</h1>
              <h2>About the book</h2>
              <br>
              <p>Whether you're new to web development or a more seasoned developer looking to refine your skills. The CSS Guide will take you from beginner to expert!</p><br>
              <p>We'll cover the basics from specificity &#38; selectors right through to the modern layout methods of flexbox &#38; grid. We'll also be diving into advanced topics such as CSS animation, architecture &#38; more!</p>
              <br><p>Available in PDF, EPUB &amp; MOBI. 🎉</p>
              <br><a href="https://gum.co/the-css-guide" target="_blank"><button>Buy now!</button></a>
              <br><br><p class="italic">* Secured payment with Gumroad.</p>
          </div>
          <div>
            <img src="https://www.easeout.co/images/uploads/the-css-guide-mockup.png" class="book-image" alt="CSS Guide cover mockups" />
          </div>
          <div class="book-contents">
            <h2>Table of Contents</h2>
              <br>
            <ul>
              <li class="chapter">Intro to CSS</li>
                <ul>
                  <li>What is CSS?</li>
                  <li>Adding CSS to your projects</li>
                </ul>
              <li class="chapter">Specificity</li>
                <ul>
                  <li>The Cascade</li>
                  <li>Inheritance</li>
                  <li>Specificty</li>
                </ul>
              <li class="chapter">Selectors</li>
                <ul>
                  <li>Selecting Elements</li>
                  <li>Attribute Selectors</li>
                  <li>Pseudo Classes</li>
                  <li>Pseudo Elements</li>
                </ul>
              <li class="chapter">Fundamentals</li>
                <ul>
                  <li>The Box Model</li>
                  <li>Margins</li>
                  <li>Padding</li>
                  <li>Borders</li>
                  <li>Commenting</li>
                  <li>Colors</li>
                    <ul>
                      <li>Hex</li>
                      <li>RGB/RGBa</li>
                      <li>HSL/HSLa</li>
                      <li>Keywords</li>
                    </ul>
                  <li>Backgrounds</li>
                  <li>Units</li>
                    <ul>
                      <li>Pixels</li>
                      <li>Em</li>
                      <li>Rem</li>
                      <li>Percentages</li>
                      <li>Viewport Units</li>
                    </ul>
                  <li>Fonts</li>
                  <li>Styling Lists</li>
                  <li>Calc</li>
                </ul>
              <li class="chapter">Layout</li>
                <ul>
                  <li>The Display Property</li>
                  <li>Positioning</li>
                  <li>z-index</li>
                  <li>Flexbox</li>
                  <li>Grid</li>
                  <li>Centering</li>
                  <li>Media Queries</li>
                </ul>
              <li class="chapter">Animating your CSS</li>
                <ul>
                  <li>Filters</li>
                  <li>Transforms</li>
                  <li>Transitions</li>
                  <li>Animations</li>
                </ul>
              <li class="chapter">CSS Architecture</li>
                <ul>
                  <li>Feature Queries</li>
                  <li>Variables</li>
                  <li>Resets &#38; Normalization</li>
                  <li>Vendor Prefixing</li>
                </ul>
            </ul>
          </div>
          <div>
            <h2>Technical Details</h2>
            <br>
            <ul class="book-details">
              <li>158 pages</li>
              <li>Available in PDF, EPUB &#38; MOBI Formats</li>
              <li>Updated December 2020</li>
            </ul>
          </div>
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
    await store.commit("SET_TITLE", "The CSS Guide");
    await store.commit("SET_CRUMB", 'Books');
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
      title: "The CSS Guide | " + this.$store.state.siteInfo.sitename,
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'The Complete Guide to Modern CSS.'
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

p {
  line-height: 1.5;
}

.book-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
  justify-items: center;
}

.book-grid h2:first-of-type{
  padding-top: 0.5em;
}

@media only screen and (max-width: 1000px) {
  .book-grid {
    grid-template-columns: 1fr;
  }
}

@media only screen and (max-width: 600px) {
  .book-grid {
    grid-template-columns: 1fr;
  }
}

.book-image {
  max-height: 550px;
  padding-top: 2em;
}

.book-details {
  padding-bottom: 3em;
}

/* BUY BUTTON */

button {
  background-color: #5585ff;
  position: relative;
  height: 50px;
  width: 200px;
  background-image: none;
  border: none;
  outline: none;
  color: white;
  font-size: 15px;
  letter-spacing: 1px;
  cursor: pointer;
  border-radius: 30px;
  font-weight: 600;
  transition: all ease-out 0.5s;
}
button:hover {
  transition: .3s;
  background-color: #95DEE3;
  box-shadow: 8px 8px #99bdff;
}

.italic {
  font-style: italic;
}

.book-contents {
  /* background-color: #fff; */
  background-color: #EFEFEF;
  border: 1px solid black;
  width: 100%;
  padding: 0 0 2em 1em;
}

.book-contents h2 {
  text-align: center;
}

.chapter {
  font-size: 110%;
  padding: 0.5em 0 0.5em 0;
}

</style>