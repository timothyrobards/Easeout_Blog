<template>
  <div class="zap-slideout xs-border xs-text-6 md-text-5" :class="{ isOpen: $store.state.menuIsActive  }">
    <div class="zap-slideout-opener">
      <div @click="toggle" class="hamburger hamburger--spin js-hamburger" :class="{'is-active': $store.state.menuIsActive }">
        <div class="hamburger-box">
          <div class="hamburger-inner"></div>
        </div>
      </div>
    </div>
    <ul class="zap-slideout-menu list-unstyled">
      <!-- <li class="zap-slideout-menu-item"> 
        <nuxt-link to="/" exact>
          <img style="width:60%" class="xs-block xs-fit xs-mb2 nav-logo" v-if="this.$store.state.siteInfo.siteicon  && this.$store.state.siteInfo.showmenu" :src="this.$store.state.siteInfo.siteicon" :alt="menuSiteName">
        </nuxt-link>
      </li> -->
      <!-- <li class="zap-slideout-menu-item--small">
        <nuxt-link to="/" exact>Home</nuxt-link>
      </li> -->
      <li class="spacer-sub--small"></li>
      <li class="zap-slideout-menu-item--small">
        Menu
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick tag-article text-white">
        <nuxt-link to="/category/article/" exact>Articles</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick tag-inspo text-white">
        <nuxt-link to="/category/inspiration/" exact>Inspiration</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick tag-template text-white">
        <nuxt-link to="/category/template/" exact>Templates</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick tag-news text-white">
        <nuxt-link to="/category/newsletter/" exact>News</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick tag-books text-white">
        <nuxt-link to="/books/" exact>Books</nuxt-link>
      </li>
      <li class="spacer-sub"></li>
      <li class="zap-slideout-menu-item--small">
        Tutorials
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary tag-css text-black">
        <nuxt-link to="/category/css/" exact>CSS</nuxt-link>
      </li> 
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary p-left tag-sass text-white">
        <nuxt-link to="/category/sass/" exact>SASS</nuxt-link>
      </li> 
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary tag-html text-white">
        <nuxt-link to="/category/html/" exact>HTML</nuxt-link>
      </li> 
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary p-left tag-git text-white">
        <nuxt-link to="/category/html/" exact>GIT</nuxt-link>
      </li> 
      <!-- <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary text-black p-left">
        <nuxt-link to="/category/javascript" exact>JavaScript</nuxt-link>
      </li> -->
      <!-- <li v-if="this.$store.state.allCats" class="zap-slideout-menu-item--small nav-item-primary">
        <nuxt-link to="/category" exact>All Tags</nuxt-link>
      </li> -->
      <!-- <li v-if="menuLinks" class="xs-mt5 zap-slideout-menu-item black-font nav-item-primary">
        Links
      </li> -->
      <li class="spacer-sub"></li>
      <li class="zap-slideout-menu-item--small">
        Links
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary">
        <nuxt-link to="/page/about/" exact>About</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary p-left">
        <nuxt-link to="/page/contact/" exact>Contact</nuxt-link>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary">
        <a href="https://emailoctopus.com/lists/2c78099d-83e4-11ea-a3d0-06b4694bee2a/forms/subscribe" exact>Subscribe</a>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary p-left">
        <a href="https://twitter.com/easeoutco" exact>Twitter</a>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary">
        <a href="https://dribbble.com/easeout" exact>Dribbble</a>
      </li>
      <li class="zap-slideout-menu-item--small nav-item-primary box-shadow-thick nav-item-secondary p-left">
        <a href="https://www.pinterest.com/easeoutco/" exact>Pinterest</a>
      </li>
      <!-- <li v-if="myPages" v-for="(pg,i) in myPages" :key="`pg-${i}`" class="zap-slideout-menu-item--small nav-item-secondary box-shadow-thick">
        <nuxt-link :to="pg._path">{{pg.title}}</nuxt-link>
      </li>
      <li v-if="menuLinks" v-for="m in menuLinks" :key="m.position" class="zap-slideout-menu-item--small nav-item-secondary box-shadow-thick">
        <a :href="m.link">{{m.name}}</a>
      </li> -->
    </ul>
  </div>
</template>

  <script>
export default {
  data() {
    return {
      isOpen: false
    };
  },
  computed: {
    menuLinks() {
      return this.$store.state.siteInfo.menu;
    },
    myPages() {
      return this.$store.state.allPages;
    },

    menuSiteName() {
      return this.$store.state.siteInfo.sitename;
    }
  },
  methods: {
    open() {
      this.isOpen = true;
    },
    close() {
      this.isOpen = false;
    },
    toggle() {
      // Look for .hamburger
      this.$store.commit("toggleMenuState");

      var hamburger = document.querySelector(".hamburger");
      // On click

      // Toggle class "is-active"

      if (this.isOpen) {
        this.close();
      } else {
        this.open();
      }
    }
  }
};
</script>
  <style lang="scss">
.black-font {
  text-transform: uppercase;
  font-weight: 700;
}
.hamburger {
  padding: 4.1em 15px;
  display: inline-block;
  cursor: pointer;
  transition-property: opacity, filter;
  transition-duration: 0.15s;
  transition-timing-function: linear;
  font: inherit;
  color: inherit;
  text-transform: none;
  background-color: transparent;
  border: 0;
  margin: 0;
  overflow: visible;
}
.hamburger:hover {
  opacity: 0.7;
}

@media only screen and (max-width: 830px) {
  .hamburger {
    padding: 4.4em 15px;
  }
}

.hamburger-box {
  width: 40px;
  height: 24px;
  display: inline-block;
  position: relative;
}

.hamburger-inner {
  display: block;
  top: 50%;
  margin-top: -2px;
}
.hamburger-inner,
.hamburger-inner::before,
.hamburger-inner::after {
  width: 40px;
  height: 4px;
  background-color: #000;
  border-radius: 4px;
  position: absolute;
  transition-property: transform;
  transition-duration: 0.15s;
  transition-timing-function: ease;
}
.hamburger-inner::before,
.hamburger-inner::after {
  content: "";
  display: block;
}
.hamburger-inner::before {
  top: -10px;
}
.hamburger-inner::after {
  bottom: -10px;
}

.hamburger--spin .hamburger-inner {
  transition-duration: 0.22s;
  transition-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
}
.hamburger--spin .hamburger-inner::before {
  transition: top 0.1s 0.25s ease-in, opacity 0.1s ease-in;
}
.hamburger--spin .hamburger-inner::after {
  transition: bottom 0.1s 0.25s ease-in,
    transform 0.22s cubic-bezier(0.55, 0.055, 0.675, 0.19);
}

.hamburger--spin.is-active .hamburger-inner {
  transform: rotate(225deg);
  transition-delay: 0.12s;
  transition-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
}
.hamburger--spin.is-active .hamburger-inner::before {
  top: 0;
  opacity: 0;
  transition: top 0.1s ease-out, opacity 0.1s 0.12s ease-out;
}
.hamburger--spin.is-active .hamburger-inner::after {
  bottom: 0;
  transform: rotate(-90deg);
  transition: bottom 0.1s ease-out,
    transform 0.22s 0.12s cubic-bezier(0.215, 0.61, 0.355, 1);
}
.zap-slideout {
  position: fixed;
  right: 0;
  top: 0;
  width: 33vw;
  height: 100vh;
  z-index:1000;
  padding: 16px;
  background-color: #fff;
  transform: translate3D(100%, 0, 0);
  transition: transform 0.6s;

  &.isOpen {
    transform: translate3D(0, 0, 0);
    transition: transform 0.6s;
  }
}

@media only screen and (max-width: 850px) {
  .zap-slideout {
    width: 45vw;
  }
}

@media only screen and (max-width: 650px) {
  .zap-slideout {
    width: 100vw;
  }
}

.zap-slideout-opener {
  position: absolute;
  top: -4px;
  right: 100%;
  transform: scale(0.5);
  margin-right: 0px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #000;
  cursor: pointer;

  &:hover {
    text-decoration: underline;
  }
}

@media only screen and (max-width: 650px) {
  .zap-slideout {
    &.isOpen {
      .zap-slideout-opener{
        right: 0 !important;
      }
    }
  }
}

.zap-slideout-menu {
  font-weight: 600;
  transition: transform 1.6s ease(out-cubic);
}

.zap-slideout-menu-item,
.zap-slideout-menu-item--small {
  cursor: pointer;
  text-transform: uppercase;

  &:hover {
    text-decoration: underline;
  }

  & + & {
    margin-top: 20px;
  }
}

.zap-slideout-menu-item {
  & + .zap-slideout-menu-item--small {
    margin-top: 30px;
  }
}

.zap-slideout-menu-item--small {
  font-weight: normal;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

/* The famed Zap agency logo (TM) */
.zap-emoji {
  height: 120px;
}

.nav-logo {
  margin: 0 auto;
}

.nav-item-primary a {
  color: #ff6060;
  padding: 0 5px 0 5px;
  text-decoration:none !important;
  letter-spacing: 2px;
  font-size: 2rem;
  font-weight: 600;
  line-height: 34px;
}

.nav-item-primary {
  background-color: #2e2e2e;
  text-align: center;
  width: 98%;
}

.nav-item-secondary a {
  color: #ff6060;
  padding: 0 5px 0 5px;
  text-decoration:none !important;
  letter-spacing: 1px;
  font-size: 1rem;
  font-weight: 600;
  line-height: 22px;
}

.nav-item-secondary {
  background-color: #ffff00;
  text-align: center;
  width: 47%;
  display: inline-block !important; 
  margin-top: 10px !important;
}

.p-left{
  margin-left: 0.5rem;
}

.spacer{
  margin-top: 1rem;
}

.spacer-sub{
  margin-top: 3rem;
}

.spacer-sub--small {
  margin-top: 0.3rem;
}

@media only screen and (max-width: 450px) {
  .spacer-sub--small {
    margin-top: 1.5rem;
  }
}

.text-black a{
  color: #282C34;
}

.text-white a{
  color: #FFF6E5;
}

/* BOX SHADOWS
*********************/
.box-shadow, .box-shadow-thick, .box-shadow-fat, .box-shadow-double, .box-shadow-triple, .box-shadow-quad, .box-shadow-bottom, .box-shadow-right { 
	display: block; margin-bottom: 0.75em; 
}
.box-shadow:after, .box-shadow-thick:after, .box-shadow-fat:after, .box-shadow-double:after, .box-shadow-triple:after, .box-shadow-quad:after, .box-shadow-bottom:after, .box-shadow-right:after {
	display: block; content: ''; clear: both;
}
.box-shadow { box-shadow: 5px 5px 0 #000; }
.box-shadow-thick { box-shadow: 8px 8px 0 #000; }
.box-shadow-fat { box-shadow: 12px 12px 0 #000; }
.box-shadow-double { box-shadow: 5px 5px 0 #000, 10px 10px 0 #2E2E2E; }
.box-shadow-triple { box-shadow: 5px 5px 0 #000, 10px 10px 0 #2E2E2E, 15px 15px 0 #585858; }
.box-shadow-quad { box-shadow: 4px 4px 0 #000, 8px 8px 0 #2E2E2E, 12px 12px 0 #585858, 16px 16px 0 #848484; }
.box-shadow-bottom { box-shadow: 0px 8px 0 #000; }
.box-shadow-right { box-shadow: 8px 0 #000; }

</style>
