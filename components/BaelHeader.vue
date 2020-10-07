<template>
  <nav ref="navBar" id="navbar" class="sm-border-bottom">
    
    <div class="topbar">
      <p>👉 Get
      <nuxt-link to="/books/the-css-guide" class="promo-link" exact>The CSS Guide</nuxt-link> book. Available now! 🎉🎉</p>
    </div>

    <div class="r">

      <!-- <div class="c-4 xs-text-left sm-border-right"> -->
      <div class="c-3 xs-text-left">
        <div>
          <!-- <nuxt-link class="sitename" to="/" exact>{{headerSiteName}}</nuxt-link> -->
          <nuxt-link class="sitename" to="/" exact><img class="easeout-logo" src="~/assets/easeout-logo.svg" alt="Easeout Logo" /></nuxt-link>
        </div>
      </div>

      <!-- <div class="c-4 xs-border-top xs-border-bottom sm-border-top-none sm-border-bottom-none sm-border-left sm-border-right xs-p2 center"> -->
      <div class="c-6 center">  
        <ul class="intro-links list-horizontal">
            <li><nuxt-link to="/category/article/" exact>Articles</nuxt-link></li>
            <li>&nbsp; <nuxt-link to="/books/" exact>Books</nuxt-link></li>
            <li>&nbsp; <nuxt-link to="/category/css/" exact>CSS</nuxt-link></li>
            <li>&nbsp; <nuxt-link to="/category/inspiration/" exact>Inspiration</nuxt-link></li>
            <li>&nbsp; <nuxt-link to="/category/newsletter/" exact>News</nuxt-link></li>
            <li>&nbsp; <nuxt-link to="/category/template/" exact>Templates</nuxt-link></li>
        </ul>
        <!-- <div class="item xs-flex">
          <VueFuse placeholder="Search" :compResults="compResults" :keys="keys" :list="allPosts" event-name="searchChanged" />
        </div> -->

      </div>
      <div v-if="blogtitle" style="z-index:55;" class="c-12 xs-border-top xs-border-bottom xs-p2 xs-text-6 titlebar">
        <div class="item">
          <nuxt-link to="/" exact>Home</nuxt-link>
          <span v-show="crumb"> &nbsp;
            <span class="text-gray-lightest"> > </span> &nbsp; {{thecrumb}} </span> &nbsp;
          <span class="text-gray-lightest"> > </span> &nbsp; {{blogtitle}}
        </div>
      </div>
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

</style>