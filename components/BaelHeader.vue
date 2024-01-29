<template>
  <nav ref="navBar" id="navbar" class="sm-border-bottom">
    
    <div class="topbar">
      <!-- <p>👉 Get -->
      <!-- <nuxt-link to="/books/the-css-guide" class="promo-link" exact>The CSS Guide</nuxt-link> ebook. Available now! 🎉🎉</p> -->
      <!-- <p>🚨 The
      <nuxt-link to="/books/getting-sassy" class="promo-link" exact>GETTING SASSY</nuxt-link> guide is now available! 🚨</p> -->
      <p>👉&nbsp;
      <nuxt-link to="/books/mastering-javascript" class="promo-link" exact>Mastering JavaScript</nuxt-link> is available now! 🎉🎉</p>
    </div>

    <div class="r">

      <!-- <div class="c-4 xs-text-left sm-border-right"> -->
      <div class="c-3 xs-text-left">
        <div>
          <!-- <nuxt-link class="sitename" to="/" exact>{{headerSiteName}}</nuxt-link> -->
          <nuxt-link class="sitename" to="/" exact><img class="easeout-logo" src="~/assets/easeout-logo-new.png" alt="Easeout Logo" /></nuxt-link>
        </div>
      </div>

      <!-- <div class="c-4 xs-border-top xs-border-bottom sm-border-top-none sm-border-bottom-none sm-border-left sm-border-right xs-p2 center"> -->
      <div class="c-6 center" v-cloak>  
        <ul class="intro-links list-horizontal">
            <li><nuxt-link to="/freelance/" exact>Freelance</nuxt-link></li> 
            <li><nuxt-link to="/books/" exact>Guides</nuxt-link></li>
            <li>Tutorials
            <ul>
                <li><nuxt-link to="/category/css/" exact>CSS</nuxt-link></li>
                <li><nuxt-link to="/category/javascript/" exact>JavaScript</nuxt-link></li>
                <li><nuxt-link to="/category/html/" exact>HTML</nuxt-link></li>
                <li><nuxt-link to="/category/sass/" exact>SASS</nuxt-link></li>
                <li><nuxt-link to="/category/git/" exact>GIT</nuxt-link></li>
                <li><nuxt-link to="/category/react/" exact>React</nuxt-link></li>
              </ul>
            </li>
            <li>More
              <ul>
                <li><nuxt-link to="/category/inspiration/" exact>Inspiration</nuxt-link></li>
                <li><nuxt-link to="/category/template/" exact>Templates</nuxt-link></li>
                <li><nuxt-link to="/page/about/" exact>About</nuxt-link></li> 
                <li><nuxt-link to="/advertise/" exact>Advertise</nuxt-link></li> 
                <li><nuxt-link to="/page/contact/" exact>Contact</nuxt-link></li>
                <li><a href="https://easeout.eo.page/news">Subscribe</a></li>
                <li><a href="https://twitter.com/easeoutco">X</a></li>
              </ul>
            </li>
            
            <!-- <li>&nbsp; <nuxt-link to="/category/template/" exact class="highlight">Freelancing</nuxt-link></li> -->
        </ul>
        <!-- <div class="item xs-flex">
          <VueFuse placeholder="Search" :compResults="compResults" :keys="keys" :list="allPosts" event-name="searchChanged" />
        </div> -->

      </div>
      <!-- <div v-if="blogtitle" style="z-index:55;" class="c-12 xs-border-top xs-border-bottom xs-p2 xs-text-6 titlebar">
        <div class="item">
          <nuxt-link to="/" exact>Home</nuxt-link>
          <span v-show="crumb"> &nbsp;
            <span class="text-gray-lightest"> > </span> &nbsp; {{thecrumb}} </span> &nbsp;
          <span class="text-gray-lightest"> > </span> &nbsp; {{blogtitle}}
        </div>
      </div> -->
    </div>
  </nav>
</template>
<script>
import VueFuse from "~/components/VueFuse";
export default {
  props: ["blogtitle", "posts", "thecrumb"],
  data() {
    return {
      results: [],
      keys: [
        {
          name: "title",
          weight: 0.3
        },
        {
          name: "body",
          weight: 0.7
        }
      ],

      compResults: []
    };
  },
  components: { VueFuse },
  computed: {
    allPosts() {
      let posts = this.$store.state.blogPosts;
      let pages = this.$store.state.allPages;
      let both = posts.concat(pages);
      return both;
    },
    headerSiteName() {
      return this.$store.state.siteInfo.sitename;
    },
    componentResults() {
      return this.$store.state.results;
    },
     crumb() {
      return this.$store.state.theCrumb;
    }
  },

  methods: {

    navHeight() {
      var height = document.getElementById("navbar").clientHeight;
      console.log(height);
      this.$store.commit("SET_NAVHEIGHT", height - 1);
 
    }
  },

  mounted() {
    this.$on("searchChanged", results => {
      this.compResults = results;
    });
  }
};
</script>
<style>
[v-cloak] { 
  display: none; 
} 
#navbar {z-index:999;}
.titlebar .item {
  overflow-x: none;
}
.results {
  padding-left: 0;
  transform: translateY(17px);
  width: 30vw;
}
.results li {
  list-style-type: none;
  margin-left: 0;
}
nav {
  position: fixed;
  background: #fff;
  top: 0;
  left: 0;
  right: 0;
}
.sitename {
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  text-transform: uppercase;
  font-weight: 900;
  font-size: 24px;
  letter-spacing: 2px;
  -webkit-text-stroke-color: #000;
  -webkit-text-stroke-width: 0.05em;
  -webkit-text-fill-color: #fff;
}

.easeout-logo {
  height: 50px;
  width: auto;
  margin: 5px 0 0 5px;
}

input.search {
  background-color: #fff !important;
}

.center{
  align-self: center;
  border-left: none !important;
  text-align: center;
}
@media only screen and (max-width: 40rem) {
  .results {
    width: 94vw;
  }
}

.topbar {
  display: grid;
  place-items: center;
  background: #C400FF; 
  background: transparent linear-gradient(90deg, #C400FF 0%, #0031FF 100%) 0% 0% no-repeat padding-box;
  opacity: 1;
  color: #FFF;
  padding: 0.5em;
  text-align: center;
}

.promo-link {
  color: white;
  text-decoration: underline;
}

.intro-links {
  /* margin: 2.5em auto 0em; */
  text-align: center;
  font-size: 1em;
  background: transparent;
  text-transform: uppercase;
}

.intro-links a {
  color: #000;
  text-decoration: none;
  display: block;
  width: 100%;
  height: 100%;
}

@media (max-width: 1024px) {
  .intro-links, .c-6.center {
    display: none;
  }
}

.intro-links a:hover {
  color: darkslategrey;
}

/* .intro-links li {
  padding-left: .25em;
} */

.intro-links:first-of-type {
  padding-left: 0em;
}

ul.list-horizontal { text-align: center;}
ul.list-horizontal li { display: inline-block; }

.intro-links a.highlight{
  background: linear-gradient(to right, #6441A5 0%, #6441A5 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 600;
}

/* Drop down menu styles */

ul.intro-links {
  list-style: none;
  height: 35px;
  line-height: 250%;
  display: inline-block;
}

ul.intro-links li {
  float: left;
  width: 120px;
}

ul.intro-links > li:hover {
  background-color: #fff; 
  cursor: pointer;
}
/* ul.intro-links > li:hover > a {
  color: purple;
} */
ul.intro-links > li > ul {
  list-style: none;
  padding: 0;
  margin: 0;
  height: 40px;
  display: none;
}
ul.intro-links > li:hover > ul {
  display: block;
}
ul.intro-links > li > ul > li {
  background-color: #fff;
  position: relative;
  z-index: 999;
  outline: 1px dashed black;
}
ul.intro-links > li > ul > li:hover {
  background-color: yellow;
}
/* ul.intro-links > li > ul > li:hover > a {
  color: green;
} */

/* Change this in order to change the Dropdown symbol */
/* li > a:after { content:  ' +'; }
li > a:only-child:after { content: ''; } */

</style>