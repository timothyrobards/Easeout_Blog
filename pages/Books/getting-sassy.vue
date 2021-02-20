<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(75vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
      <div class="item xs-block xs-full-height">
        <div class="book-grid">
          <div>
              <h1 class="xs-py3 main-title">Getting SASSY</h1>
              <h2>About the book</h2>
              <br>
              <p>Are you ready to take your web development skills to the next level?</p><br>
              <p>The Getting SASSY guide will take you there! By learning SASS, your front-end development will be much more organized, faster and highly maintainable.</p><br>
              <p>We'll cover the basics from variables, nesting, mixins, for/each loops and much more! We'll also take an in-depth look at how to structure your projects, as well as how to go about creating a build process that you can use for all your future projects!</p><br>
              <br><p>Available in PDF, EPUB &amp; MOBI. 🎉</p>
              <br><a href="https://gum.co/getting-sassy" target="_blank"><button>Buy now!</button></a>
              <br><br><p class="italic">* Secured payment with Gumroad.</p>
          </div>
          <div>
            <img src="https://www.easeout.co/images/uploads/getting-sassy-mockup.png" class="book-image" alt="Getting SASSY cover mockup" />
          </div>
          <div class="book-contents">
            <h2>Table of Contents</h2>
              <br>
            <ul>
              <li class="chapter">Introducing SASS</li>
                <ul>
                  <li>Defining CSS Preprocessors</li>
                  <li>Why use Preprocessors?</li>
                  <li>What is SASS?</li>
                  <li>SCSS or Sass?</li>
                </ul>
              <li class="chapter">Setting up SASS</li>
                <ul>
                  <li>Environment Setup</li>
                  <li>Folder Structure</li>
                  <li>File Structure</li>
                  <li>Initializing our Project Directory</li>
                  <li>Install node-sass</li>
                  <li>Compiling Sass code to CSS</li>
                  <li>Live Reload</li>
                </ul>
              <li class="chapter">Variables</li>
                <ul>
                  <li>What are Variables?</li>
                  <li>Variables in Action</li>
                </ul>
              <li class="chapter">Nesting</li>
                <ul>
                  <li>What is Nesting?</li>
                  <li>Nesting in Action</li>
                </ul>
              <li class="chapter">Mixins</li>
                <ul>
                  <li>What are Mixins?</li>
                  <li>Common Use Cases</li>
                </ul>
              <li class="chapter">Functions</li>
                <ul>
                  <li>What are Functions?</li>
                  <li>Function Examples</li>
                </ul>
              <li class="chapter">Partials and Importing</li>
                <ul>
                  <li>Using Partials</li>
                  <li>@import in CSS vs SASS</li>
                </ul>
              <li class="chapter">Inheritance</li>
                <ul>
                  <li>What is Inheritance?</li>
                  <li>Examples of Inheritance</li>
                </ul>
              <li class="chapter">The Ampersand Operator</li>
                <ul>
                  <li>What is the SASS Ampersand Operator?</li>
                </ul>
              <li class="chapter">Control Directives</li>
                <ul>
                  <li>@if and @else/li>
                  <li>@for</li>
                  <li>@while</li>
                </ul>
              <li class="chapter">Interpolation</li>
                <ul>
                  <li>Understanding the Syntax</li>
                  <li>Why use Interpolation?</li>
                </ul>
              <li class="chapter">Placeholders</li>
                <ul>
                  <li>Why use Placeholders?</li>
                </ul>
              <li class="chapter">Structuring your SASS Projects</li>
                <ul>
                  <li>How do we structure our SASS projects?</li>
                  <li>Simple Structure</li>
                  <li>The 7-1 Pattern</li>
                  <li>Get up and running with 7-1</li>
                </ul>
              <li class="chapter">Setting up Media Queries with SASS</li>
                <ul>
                  <li>Setting up your mixins</li>
                  <li>Using a Mixin</li>
                  <li>Another way to set up our Mixins</li>
                </ul>
              <li class="chapter">Setting up the Perfect Build Process</li>
                <ul>
                  <li>What is a Build Process?</li>
                  <li>Creating the Build Process!</li>
                </ul>
              <li class="chapter">Conclusion</li>
            </ul>
          </div>
          <div>
            <h2>Technical Details</h2>
            <br>
            <ul class="book-details">
              <li>55 pages</li>
              <li>Available in PDF, EPUB &#38; MOBI Formats</li>
              <li>Updated February 2021</li>
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
    await store.commit("SET_TITLE", "Getting SASSY");
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
      title: "Getting SASSY | " + this.$store.state.siteInfo.sitename,
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'A Practical Guide to SASS.'
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