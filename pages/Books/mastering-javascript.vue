<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(75vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
      <div class="item xs-block xs-full-height">
        <div class="book-grid">
          <div>
              <h1 class="xs-py3 main-title">Mastering JavaScript</h1>
              <h2>About the book</h2>
              <br>
              <p>JavaScript is one of the most powerful programming languages on the web! With it, you can build highly dynamic websites and apps (including both frontend and backend development!).</p><br>
              <p>Have you ever wanted to learn Angular, React, Vue or Node.js? A solid understanding of JavaScript fundamentals will make picking up JS frameworks a breeze!</p><br>
              <p>We cover it all from basic Syntax & Structure, Variables and Data Types to the Document Object Model (the DOM), Arrays, Functions, Loops, and Objects. We also dive into advanced topics such as working with APIs, Async and Defer, Promises, Regex operations & more!</p><br>
              <p>Mastering JavaScript will benefit your web development skills enormously - and it's in very high demand professionally, today the average salary for JavaScript developers are some of the highest in tech!</p><br>
              <br><p>Available in PDF, EPUB &amp; MOBI. 🎉</p>
              <br><a href="https://gum.co/mastering-javascript" target="_blank"><button>Buy now!</button></a>
              <br><br><p class="italic">* Secured payment with Gumroad.</p>
          </div>
          <div>
            <img src="https://www.easeout.co/images/uploads/getting-sassy-mockup.png" class="book-image" alt="Mastering JavaScript cover mockup" />
          </div>
          <div class="book-contents">
            <h2>Table of Contents</h2>
              <br>
            <ul>
              <li class="chapter">Introducing JavaScript</li>
                <ul>
                  <li>How to add JavaScript to a webpage</li>
                  <li>How to add inline JavaScript</li>
                  <li>How to link to external JavaScript</li>
                </ul>
              <li class="chapter">Syntax and Structure</li>
                <ul>
                  <li>Values</li>
                  <li>Camel Case</li>
                  <li>Unicode</li>
                  <li>Semicolons</li>
                  <li>Indentation</li>
                  <li>White space</li>
                  <li>Commenting</li>
                  <li>Identifiers</li>
                  <li>Case sensitivity</li>
                  <li>Reserved words</li>
                  <li>JavaScript Operators</li>
                  <li>JavaScript Expressions</li>
                </ul>
              <li class="chapter">Variables, Scope and Hoisting</li>
                <ul>
                  <li>What are Variables?</li>
                  <li>Naming Variables</li>
                  <li>Difference between var, let and const</li>
                  <li>Variable scope</li>
                  <li>Hoisting</li>
                  <li>Constants</li>
                </ul>
              <li class="chapter">Data Types</li>
                <ul>
                  <li>What are Data Types?</li>
                </ul>
              <li class="chapter">Converting Data Types</li>
                <ul>
                  <li>Converting Values to Strings</li>
                  <li>Converting Values to Numbers</li>
                  <li>Converting Values to Booleans</li>
                </ul>
              <li class="chapter">The Basics of JavaScript Strings</li>
                <ul>
                  <li>Creating Strings</li>
                  <li>Concatenation</li>
                  <li>Syntax rules</li>
                </ul>
              <li class="chapter">Working with Strings</li>
                <ul>
                  <li>The Anatomy of a String</li>
                  <li>Converting Strings into Numbers</li>
                </ul>
              <li class="chapter">An Introduction to the DOM</li>
                <ul>
                  <li>What is the DOM?</li>
                  <li>The DOM Tree and Nodes</li>
                </ul>
              <li class="chapter">Accessing DOM Elements</li>
                <ul>
                  <li>getElementById()</li>
                  <li>getElementsByClassName()</li>
                  <li>getElementsByTagName()</li>
                  <li>Query Selectors</li>
                </ul>
              <li class="chapter">Traversing the DOM</li>
                <ul>
                  <li>Root Nodes</li>
                  <li>Parent Nodes</li>
                  <li>Child Nodes</li>
                  <li>Sibling Nodes</li>
                </ul>
              <li class="chapter">Making changes to the DOM</li>
                <ul>
                  <li>Creating New Nodes</li>
                  <li>Inserting Nodes into the DOM</li>
                  <li>Removing Nodes from the DOM</li>
                </ul>
              <li class="chapter">How to modify DOM Nodes</li>
                <ul>
                  <li>Modifying Attributes</li>
                  <li>Modifying Classes</li>
                  <li>Modifying Styles</li>
                </ul>
              <li class="chapter">Understanding Events</li>
                <ul>
                  <li>What are Event Handlers and Listeners?</li>
                  <li>Inline Event Handlers</li>
                  <li>Event Handler Properties</li>
                  <li>Event Listeners</li>
                  <li>Common Events</li>
                  <li>Event Objects</li>
                </ul>
              <li class="chapter">Mastering Arrays</li>
                <ul>
                  <li>Creating an Array</li>
                  <li>Looping over an Array</li>
                  <li>Adding to an Array</li>
                  <li>Removing from an Array</li>
                  <li>Array indexes/li>
                  <li>Additional Array Operations</li>
                  
                </ul>
              <li class="chapter">Mastering Objects</li>
                <ul>
                  <li>Creating an Object</li>
                  <li>Understanding the syntax</li>
                  <li>Updating Objects</li>
                  <li>Understanding 'this' in an Object</li>
                </ul>
              <li class="chapter">Using Conditionals</li>
                <ul>
                  <li>if/else statements</li>
                  <li>else if</li>
                  <li>Comparison Operators</li>
                  <li>Nesting</li>
                  <li>Logical Operators</li>
                  <li>Switch statements</li>
                  <li>The Ternary Operator</li>
                </ul>
              <li class="chapter">Mastering Loops</li>
                <ul>
                  <li>The for loop</li>
                  <li>The do ... while statement</li>
                  <li>Labelled, break and continue</li>
                  <li>for in and for of</li>
                </ul>
              <li class="chapter">Mastering Functions</li>
                <ul>
                  <li>Defining Functions</li>
                  <li>Function Expressions</li>
                  <li>Calling Functions</li>
                  <li>Function Scope</li>
                  <li>Nesting and Closures</li>
                  <li>Arguements Object</li>
                  <li>Function Parameters</li>
                  <li>Arrow Functions</li>
                  <li>Predefined Functions</li>
                </ul>
              <li class="chapter">What are Classes?</li>
                <ul>
                  <li>Class Declairations</li>
                  <li>Class Expressions</li>
                  <li>Constructors</li>
                  <li>Other useful Class properties</li>
                </ul>
              <li class="chapter">Understanding APIs</li>
                <ul>
                  <li>APIs in JavaScript</li>
                  <li>How do API's work?</li>
                </ul>
              <li class="chapter">Fetching data from a server</li>
                <ul>
                  <li>The old way</li>
                  <li>The solution: AJAX</li>
                  <li>Creating an AJAX request</li>
                  <li>XMLHttpRequest</li>
                  <li>Fetch</li>
                </ul>
              <li class="chapter">An Introduction to REST APIs</li>
                <ul>
                  <li>What is a REST API?</li>
                  <li>RESTful Architecture</li>
                  <li>REST in action</li>
                  <li>Working with REST data</li>
                </ul>
              <li class="chapter">Promises</li>
                <ul>
                  <li>Why use Promises?</li>
                </ul>
              <li class="chapter">Async and Defer</li>
                <ul>
                  <li>What are the methods?</li>
                  <li>Why use each method?</li>
                </ul>
              <li class="chapter">The 'this' keyword</li>
                <ul>
                  <li>What is 'this'?</li>
                  <li>Examples of execution contexts</li>
                </ul>
              <li class="chapter">Understanding Regex</li>
                <ul>
                  <li>A very basic regex pattern</li>
                  <li>Why use Regular Expressions?</li>
                  <li>Creating a Regular Expression</li>
                  <li>Regular expression methods</li>
                  <li>The power of Regex</li>
                  <li>Flags</li>
                  <li>Character Groups</li>
                </ul>
              <li class="chapter">Conclusion</li>
            </ul>
          </div>
          <div>
            <h2>Technical Details</h2>
            <br>
            <ul class="book-details">
              <li>226 pages</li>
              <li>Available in PDF, EPUB &#38; MOBI Formats</li>
              <li>Updated for 2022!</li>
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