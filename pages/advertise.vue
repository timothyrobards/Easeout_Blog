<template>
  <main>
    <div class="full-height single xs-border-left xs-border-right" :style="`min-height:calc(75vh - ${navbarheight}px);margin-top:${navbarheight}px`">
      <div class="xs-mt2 xs-p2 bcg-item">
      <div class="item xs-block xs-full-height post-content">
          <div>
              <h1 class="xs-py3 main-title">Advertise on Easeout</h1>
              <p>Easeout is committed to providing quality content in the form of articles, tutorials, and inspiration, to a highly engaged audience of web enthusiasts. We have over 250k pageviews per month (and growing!).</p>
              <p>Advertising is a fantastic way to drive traffic to your product or service. We have several advertising spots on the site, we also offer promotional posts and the ability to sponsor our newsletter.</p>
              <p>For any enquiries <a href="mailto:hello@easeout.co">contact us</a>.</p>

              <h2>Sponsored Article</h2>
              <p>If you would like to share your content with our community, a dedicated blog post is the way to go!</p>
              <p>You will receive:</p>
              <ul>
                <li>A professionally written blog post, by our technical writer, profiling your product or service (or you may provide your own copy)</li>
                <li>Exposure to our 250k monthly pageviews</li>
                <li>Exposure to our 30,000+ RSS feed subscribers</li>
                <li>Social media post to our Twitter feed</li>
                <li>Feature in our next "Frontend News" issue (sent to our email subscribers)</li>
                <li>Plus your article will live permanently on our site</li>
              </ul>
              <p><a href="http://gum.co/easeout-article-sponsor" target="_blank"><button>Book Now</button></a></p>

              <p><em>Please note</em>: We reserve the right to cancel your order &amp; issue a refund, if your product is inappropriate for our audience.</p>
              
              <h2>Newsletter Sponsorship</h2>
              <p>Our “Frontend News” newsletter is published on a bi-weekly basis. Each issue is packed full of the latest news, which we curate for the web design and development community. The newsletter is published on our site, sent out to our email list, tweeted by us <a href="https://twitter.com/easeoutco">@easeoutco</a>, and is read by 30,000+ RSS feed subscribers.</p>
              <p>We insert a prominent ad placement for you (labelled “Our Sponsor”), which includes a title, short description, and image in the top row of our newsletter.</p>
              <p>To check availability, or for more details, <a href="mailto:hello@easeout.co">contact us</a>.</p>

              <h2>Display Advertising</h2>
              <p>We have several advertising spots available on the site. Key placements include the header and above the article content. If you're looking for display ads, please contact us directly.</p>
              <p>If you have any questions, would like to know the prices of our options, or have any ideas on how you would like to promote your product or service, please <a href="mailto:hello@easeout.co">get in touch</a> with us.</p>
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
    await store.commit("SET_TITLE", "Advertise");
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
      title: "Advertise | " + this.$store.state.siteInfo.sitename,
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'Advertise with Easeout. Target your ads to our audience of web professionals.'
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