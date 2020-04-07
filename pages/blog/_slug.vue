<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(100vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
        <div class="item xs-block xs-full-height">
          <div class="feat-wrapper" v-if="theThumb"><transition appear name="fade"><img class="featured-image" :src="thumbnail" :alt="title"></transition></div>
          <h1 class="xs-py3 main-title">{{title}}</h1>
          <no-ssr>
            <div class="xs-mt-5 bold">
            <ul class="list-unstyled xs-flex xs-flex-align-center">

              <!-- TAGS -->

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('CSS')"><div class="tag tag-css">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-black">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('Inspiration')"><div class="tag tag-inspo">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('Newsletter')"><div class="tag tag-news">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('Template')"><div class="tag tag-template">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('Article')"><div class="tag tag-article">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <!-- END TAGS -->

              <li class="xs-inline-block">{{ date }}</li>
              </ul> 
             </div>
          </no-ssr>
          <div class="xs-py3 post-content text-gray-lighter">
            <div v-html="$md.render(body)"></div>
          </div>
        </div>
      </div>

    </div>
  </main>
</template>



<script>
import MdWrapper from "~/components/MdWrapper";

export default {
  async asyncData({ params, app, payload, route, store }) {
    let post = await import("~/content/blog/posts/" + params.slug + ".json");
    console.log(post);
   
   await store.commit("SET_TITLE", post.title);
     await store.commit("SET_THUMB", post.thumbnail);
     await store.commit("SET_CRUMB", 'Blog');
   await   store.commit("SET_POSTCAT", post.category);
    await store.commit("paginateOff", false);
    return post;
  },
   transition (to, from) {
    if (!from) { return 'slide-left' } else {return 'slide-right'}
  },
  head() {
    return {
      title: this.title + " | " + this.$store.state.siteInfo.sitename,
      meta: [{
        hid: 'description',
        name: 'description',
        content: this.short
      }],
      link: [{
        rel: 'canonical',
        href: 'https://easeout.co' + this.$route.path
      }]
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
    theThumb() {
      return this.$store.state.theThumbnail;
    },
    allBlogPosts() {
      return this.$store.state.blogPosts;
    },
    navbarheight() {
      return this.$store.state.navheight;
    }
  },
  components: {
    MdWrapper
  }
};
</script>

<style>

  /* TAG STYLES */

  .tag-css {
    background-color: #95DEE3;
    border-color: #95DEE3;
  }

  .tag-article {
    background-color: #282C34;
    border-color: #282C34;
  }
  
  .tag-inspo {
    background-color: #F7786B;
    border-color: #F7786B;
  }

  .tag-news {
    background-color: #5B5EA6;
    border-color: #5B5EA6;
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

</style>
