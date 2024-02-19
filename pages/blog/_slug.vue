<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(100vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
        <div class="item xs-block xs-full-height">
          <div class="feat-wrapper" v-if="theThumb"><transition appear name="fade"><img class="featured-image" :src="thumbnail" :alt="title"></transition></div>
          
          <div class="blog-grid">
          <div class="div-article"> 

          <h1 class="xs-py3 main-title">{{title}}</h1>
          <no-ssr>
            <div class="xs-mt-5 bold">
            <ul class="list-unstyled xs-flex xs-flex-align-center">

              <!-- TAGS -->

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('CSS')"><div class="tag tag-css">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-black">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('SASS')"><div class="tag tag-sass">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('HTML')"><div class="tag tag-html">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('GIT')"><div class="tag tag-git">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-white">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('React')"><div class="tag tag-react">
                <nuxt-link :to="`/category/${this.$store.state.theCategory.toLowerCase()}/`" class="tag__link text-black">{{this.$store.state.theCategory}}</nuxt-link>
              </div></li> 

              <li class="xs-inline-block xs-mr1" v-if="this.$store.state.theCategory.includes('JavaScript')"><div class="tag tag-javascript">
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

          
              <div class="xs-py3 post-content">
                <div v-html="$md.render(body)"></div>
                <br>
                <p><img src="~/assets/timprofile.jpeg" class="profile-main-image blog-author" alt="Tim profile image" /></p>
                <h2>A little about me..</h2>
                <p>Hey, I&rsquo;m Tim! 👋</p>
                <p>I&rsquo;m a freelance business owner, web developer &amp; author. I teach both new and experienced freelancers how to build a sustainable and successful freelancing business. Check out my&nbsp;<a href="http://www.easeout.co/freelance">Complete Guide to Freelancing</a> if you'd like to find out more.</p>
                <p>While you're here, you can browse through my blogs where I post freelancing tips, code tutorials, design inspiration, useful tools & resources, and much more! You can also <a href="https://easeout.eo.page/news" target="_blank">join the newsletter</a>, or find me on <a href="https://twitter.com/easeoutco" target="_blank" rel="noopener ugc nofollow">X</a>.</p>
                <p>Thanks for reading! 🎉</p>
                </div>
              </div>

              <div class="div-ads"> 
              <br />
              <!-- My eBook-->
              <a href="https://easeout.gumroad.com/l/freelance" target="_blank"><img src="~/assets/freelance-package-ad.svg" class="center" alt="The Complete Guide to Freelancing"/>
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
              <br /><br />
              </div>
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
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.short
        },
        {name: 'twitter:card', content: 'summary'},
        {name: 'twitter:site', content: 'https://www.easeout.co' + this.$route.path},
        {name: 'twitter:title', content: this.title},
        {name: 'twitter:description', content: this.short},
        {name: 'twitter:creator', content: '@easeoutco'},
        {name: 'twitter:image:src', content: 'https://www.easeout.co' + this.thumbnail},
      ],
      link: [{
        rel: 'canonical',
        href: 'https://www.easeout.co' + this.$route.path
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


