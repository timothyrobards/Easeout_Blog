<template>
<footer class="retro-gray xs-text-6 md-text-5">
    <div class="r no-gap">

        <div class="c-12 xs-text-left xs-p2 xs-border">
            <div class="item xs-text-center">
                <div v-if="pagination" class="xs-flex xs-flex-justify-center xs-flex-align-center">
                    <span class="xs-absolute xs-l1 xs-text-6 text-gray-lighter xs-mr2 "> <span class="bold">&nbsp; {{ 1 + this.$store.state.gridOffset}} - {{this.pageCount}}</span> of {{this.$store.state.resultsnum}} </span>

                    <div class="pagination" style="padding:1rem!important;">

                        <nuxt-link :to="`?page=${prevpage}`" tag="button" :class="{ 'pagination__button--disabled': this.prevpage <= 0 }" class="pagination__button pagination__button--prev">
                            <svg class="pagination__button--prev-icon" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
      <path d="M368.619 16.892l24.485 24.449c2.938 2.934 4.897 7.335 4.897 11.246 0 3.912-1.959 8.313-4.897 11.246l-192.448 192.168 192.448 192.168c2.938 2.934 4.897 7.335 4.897 11.246 0 4.401-1.959 8.313-4.897 11.246l-24.485 24.449c-2.938 2.934-7.345 4.89-11.263 4.89s-8.325-1.956-11.263-4.89l-228.196-227.864c-2.938-2.934-4.897-7.335-4.897-11.246 0-3.912 1.959-8.313 4.897-11.246l228.196-227.864c2.938-2.934 7.345-4.89 11.263-4.89s8.325 1.956 11.263 4.89v.002z"/>
    </svg>
                        </nuxt-link>
                        <nuxt-link :to="`?page=${nextpage}`" no-prefetch tag="button" :class="{ 'pagination__button--disabled': this.queryParam >= this.totalpages }" class="pagination__button pagination__button--next">
                            <svg class="pagination__button--next-icon" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
      <path d="M142.382 16.892l-24.485 24.449c-2.938 2.934-4.897 7.335-4.897 11.246 0 3.912 1.959 8.313 4.897 11.246l192.448 192.168-192.448 192.168c-2.938 2.934-4.897 7.335-4.897 11.246 0 4.401 1.959 8.313 4.897 11.246l24.485 24.449c2.938 2.934 7.345 4.89 11.263 4.89s8.325-1.956 11.263-4.89l228.196-227.864c2.938-2.934 4.897-7.335 4.897-11.246 0-3.912-1.959-8.313-4.897-11.246l-228.196-227.864c-2.938-2.934-7.345-4.89-11.263-4.89s-8.325 1.956-11.263 4.89v.002z"/>
    </svg>
                        </nuxt-link>
                    </div>

                   

                </div>
                <div v-else></div>

            </div>

        </div>
        <!-- <div v-if="signupBoolean" class="c-25 xs-text-left xs-p2 xs-border">
            <div v-if="!sent" class="item">
                <div class="footer__heading xs-mb2">🎉 Get Easeout in your inbox 🎉</div>
                <form @submit.prevent="processForm" action="/.netlify/functions/app" name="mailinglist">
                    <input type="email" v-model="emaildata.email" class="text-input text-input--small xs-mb1 xs-mr2" placeholder="your email here">
                    <button type="submit" class="button button--transparent button--small">Subscribe</button>
                </form>
            </div>
            <div class="item" v-else>
                <div class="xs-mb2">{{emaildata.email}} has been added to our newsletter.</div>

            </div>
        </div> -->
        <div class="xs-text-center xs-p2 xs-border footer-cta" :class="signupAboutSize">
            <div class="item">
                <!-- <div v-show="siteDescription" class="footer__heading footer__heading1 xs-mb2 xs-text-3">Subscribe to Easeout</div> -->
                <!-- EMAIL OCTOPUS CODE (linked EO stylesheet in nuxt.config too) -->

                <div class="email-octopus-form-wrapper">
                    <h2 class="email-octopus-heading"></h2>
                    <p class="email-octopus-success-message"></p>
                    <p class="email-octopus-error-message"></p>

                <form method="post"
                    action="https://emailoctopus.com/lists/2c78099d-83e4-11ea-a3d0-06b4694bee2a/members/embedded/1.3/add"
                    class="email-octopus-form"
                    data-sitekey="6LdYsmsUAAAAAPXVTt-ovRsPIJ_IVhvYBBhGvRV6"
                >
        
                <div class="email-octopus-form-row">
                    <p>🤓 Want to stay up to date?</p>
                    <p>🚀 And join our community?</p>
                    <p>🎉 Subscribe to the newsletter today!</p>
                    <br>
                    <input id="field_0" name="field_0" type="email" placeholder="Your email here...">
                </div>

                <div class="email-octopus-form-row-hp" aria-hidden="true">
                    <!-- Do not remove this field, otherwise you risk bot sign-ups -->
                    <input type="text" name="hp2c78099d-83e4-11ea-a3d0-06b4694bee2a"
                        tabindex="-1"
                        autocomplete="nope">
                    </div>
                <div class="email-octopus-form-row-subscribe">
                    <input type="hidden"
                    name="successRedirectUrl"
                    value="">
                    <button type="submit" class="subbtn">Subscribe</button>
                </div>
                </form>   
                </div>

                <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.0.0/jquery.min.js"></script>
                <script src="https://emailoctopus.com/bundles/emailoctopuslist/js/1.4/formEmbed.js"></script>
                
                <!-- END EMAIL OCT CODE -->

            </div>
        </div>
        <div class="xs-text-center xs-p2 xs-border footer-right" :class="signupAboutSize">
            <div class="item">
                <div v-show="connectData" class="footer__heading xs-mb2">Links</div>
                <ul class="list-unstyled list-horizontal">
                    <li><nuxt-link to="/page/about/" exact>About</nuxt-link></li> /
                    <li><nuxt-link to="/advertise/" exact>Advertise</nuxt-link></li> /
                    <li><nuxt-link to="/page/contact/" exact>Contact</nuxt-link></li> /
                    <li><nuxt-link to="/books/" exact>Books</nuxt-link></li> /
                    <li><nuxt-link to="/freelance/" exact>Freelance</nuxt-link></li> /
                    <li><a href="https://www.easeout.co/rss.xml">RSS</a></li> /
                    <li><a href="https://twitter.com/easeoutco">X</a></li>                    
                </ul>
            </div>
            <div class="item">
                <br><br>
                <div class="footer__heading xs-mb2">Browse all topics</div>
                <ul class="list-unstyled list-horizontal">
                    <li class="tag tag-article text-white"><nuxt-link to="/category/article/" exact><div class="tag__link">Article</div></nuxt-link></li>
                    <li class="tag tag-html text-white p-left"><nuxt-link to="/category/html/" exact><div class="tag__link">HTML</div></nuxt-link></li>
                    <li class="tag tag-css text-black p-left"><nuxt-link to="/category/css/" exact><div class="tag__link">CSS</div></nuxt-link></li>
                    <li class="tag tag-javascript text-black p-left"><nuxt-link to="/category/javascript/" exact><div class="tag__link">JavaScript</div></nuxt-link></li>
                    <li class="tag tag-sass text-white p-left"><nuxt-link to="/category/sass/" exact><div class="tag__link">SASS</div></nuxt-link></li>
                    <li class="tag tag-git text-white p-left"><nuxt-link to="/category/git/" exact><div class="tag__link">GIT</div></nuxt-link></li>
                    <li class="tag tag-react text-black p-left"><nuxt-link to="/category/react/" exact><div class="tag__link">React</div></nuxt-link></li>
                    <li class="tag tag-inspo text-white p-left"><nuxt-link to="/category/inspiration/" exact><div class="tag__link">Inspiration</div></nuxt-link></li>
                    <li class="tag tag-news text-white p-left"><nuxt-link to="/category/newsletter/" exact><div class="tag__link">News</div></nuxt-link></li>
                    <li class="tag tag-template text-white p-left"><nuxt-link to="/category/template/" exact><div class="tag__link">Templates</div></nuxt-link></li> 
                    <br><br>
                </ul>
            </div>
        </div>
        <div class="c-12 xs-text-left xs-p2 xs-border">
            <div class="item xs-text-6 center"> &copy; Easeout {{ new Date().getFullYear() }}</div>
        </div>
    </div>
</footer>
</template>

<script>
export default {
    props: ["pagination"],
    watchQuery: ['page'],
    data() {
        return {
            emaildata: {
                email: ""
            },
            sent: false
        };
    },
    mounted() {
        let gumScript = document.createElement('script')
        gumScript.setAttribute('src', 'https://gumroad.com/js/gumroad.js')
        document.head.appendChild(gumScript)
    },
    methods: {

        async processForm() {
            try {
                const sendgrid = await this.$axios.post(
                    `${process.env.API_URL}/.netlify/functions/app`,
                    this.emaildata
                );
                console.log("Processed!");
                this.sent = true;
            } catch (e) {
                console.log(e);
            }
        }
    },
    computed: {
        nextCheck() {
            if (this.nextpage > this.queryParam) {
                return true
            } else {
                return false
            }
        },
        pageCount() {
            var tp = (this.$store.state.gridNumPosts * 1) + (this.$store.state.gridOffset * 1)
            if (tp > this.$store.state.resultsnum) {
                return this.$store.state.resultsnum

            } else {
                return tp + 1

            }
        },
        signupAboutSize: function () {
            return {
                "c-25": this.signupBoolean,
                "c-6": !this.signupBoolean
            };
        },
        prevpage() {
            var prev = Number(this.queryParam) - 1;
            return prev;
        },
        totalpages() {
            var res = this.$store.state.resultsnum;
            var total = Math.ceil(res / 12);
            return total;
        },
        nextpage() {
            var next = Number(this.queryParam) + 1;
            return next;
        },
        queryParam() {
            if (this.$route.query.page == null) {
                return 1;
            } else {
                return Number(this.$route.query.page);
            }
        },

        connectData() {
            return this.$store.state.connect.connectlinks;
        },
        siteDescription() {
            return this.$store.state.siteInfo.sitedescription;
        },
        signupBoolean() {
            return this.$store.state.siteInfo.emailsignup;
        }
    }
};
</script>

<style scoped>

.gumroad .cart_button {
  display: none!important;
} 

.text-input {
    max-width: 100%;
}

.footer__heading {
    max-width: 100%;
}

.center{
    text-align: center;
}

.retro-gray {
    background-color: #fff;
}

.footer-cta {
    /* background-color: #282C34;  */
    background: #C400FF; 
    background: transparent linear-gradient(90deg, #C400FF 0%, #0031FF 100%) 0% 0% no-repeat padding-box;
}

.footer-cta p, .footer__heading1 {
    /* font-family: monospace; */
    font-size: 1.2em;
    color: #f0f0f0;
    line-height: 27px;
}

.footer__heading1 {
    letter-spacing: 1.2px;
}

.subbtn {
    font-size: 1.2em;
    color: #f0f0f0;
    font-weight: 400;
    border: 1px solid #f0f0f0;
    border-radius: 4px; 
    background: transparent;
}

.subbtn:hover {      
    background-color: #C300FF;      
    color: white; 
}

@media (max-width: 640px) {
  .footer-cta p, .footer__heading1 {
    font-size: 1.2em;
  }
}

.footer-left{
    background-color: #fff;
}

.footer-right{
    background-color: #fff;
    border: 10px solid transparent !important;
}

@media (max-width: 640px) {
  .footer-right{
    font-size: 1.2em;
    line-height: 1.4;
  }
}

ul.list-horizontal { text-align: center;}
ul.list-horizontal li { display: inline-block; }

.p-left{
  margin-left: 0.25rem;
}

</style>
