<template>
  <div class="wraper" id="portfolio">
   <h2>Portfolio <span class="txt1">/</span> Showcase</h2>
   <div class="boxes">

 <div v-for="item in works" class="box" :class="{noHover: item.showModal}" :style="{background: item.img}">
       <div>
         <h4 class="title">
           <span style="font-size: 50%; text-decoration: underline">{{item.type}}</span>
           <br>
           {{item.name}}
           <i  v-if="item.modal"
                  id="show-modal"
                  @click="item.showModal = true"
                  class="fa fa-picture-o"
                  style="  border-bottom: 1px solid rgb(227, 181, 5);"
                  aria-hidden="true"></i>
          </h4>
         <div class="work-bg" :style="{background: item.bac}"></div>
         <div class="description-wraper">
           <p class="description">
             {{item.description}}<br>
             <strong>{{item.data}}</strong>
           </p>

         </div>
     </div>
     <modal v-if="item.showModal" @close="item.showModal = false">
       <carousel  v-if="item.imgs"
                  :perPage="1"
                  :navigationEnabled="true"
                  paginationActiveColor="#e3b505"
                  slot="header">
        <slide v-if="item.details" class="desktop-only">
          <div class="details" style="padding: 20px;">
            <h4 class="modal-title txt4">{{item.name}}</h4>
            <p class="serif">
              {{item.description}}
            </p>
            <div v-if="item.conception">
              <h4 class="modal-title txt1">The conception:</h4>
              <p class="serif">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
              </p>
            </div>
            <h4 v-if="item.link" class="modal-title txt4">Visit:
              <a :href="item.link" target="_blank">
                <i class="fa fa-external-link"
                   style="  border-bottom: 1px solid rgb(227, 181, 5);"
                   aria-hidden="true"></i>
              </a>
             </h4>
            <h4 style="color: rgb(240, 84, 35); padding-top: 5px; border-top: 1px solid black;">Use arrows or dots to change slide and see image assets.</h4>
          </div>
        </slide>
          <slide v-for="picture in item.imgs" class="bombka">
             <img :src="picture.img" />
          </slide>
          <slide v-if="item.iframe" class="bombka">
             <iframe class="center-block iframe" :style="{height: item.iframeHeight}" :src="item.iframe"></iframe>
          </slide>
       </carousel>

       <div class="modal-body mobile-only" slot="body">
         <h4 class="modal-title">{{item.name}}</h4>
         <p>{{item.description}}</p>
         <h4 v-if="item.link" class="modal-title">Visit:
           <a :href="item.link" target="_blank">
             <i class="fa fa-external-link"
                style="  border-bottom: 1px solid rgb(227, 181, 5);"
                aria-hidden="true"></i>
           </a>
          </h4>
         <h4 v-if="item.details" class="mobile-only">To see more details about this project visit full version of my site.</h4>
       </div>
     </modal>
   </div>
   </div>
  </div>
</template>

<script>
  import Modal from './Modal.vue'
  import { Carousel, Slide } from 'vue-carousel'
  import VueSilentbox from 'vue-silentbox'


  export default {
    components: { VueSilentbox, Carousel, Slide, Modal },
    data () {
      return {

        works: [
          {
            name: 'asseco',
            description: 'HTML5 Web Banner for Asseco Banking app.',
            details: true,
            conception: false,
            type: 'HTML5 Web Banner',
            data: '2017',
            bac: 'rgba(227, 181, 5, 0.95)',
            img: "url('./src/assets/img/works/asseco/asseco_cbp1.jpg')",
            imgs: [
              {img: "./src/assets/img/works/asseco/asseco_cbp1.jpg"},
              {img: "./src/assets/img/works/asseco/asseco_cbp2.jpg"},
              {img: "./src/assets/img/works/asseco/asseco_cbp3.jpg"},
              {img: "./src/assets/img/works/asseco/asseco_cbp4.jpg"},
              {img: "./src/assets/img/works/asseco/asseco_cbp5.jpg"},
            ],
            iframe: "src/assets/img/works/asseco/300x600/asseco_300x600.html",
            iframeHeight: '600px',
            modal: true,
            showModal: false
          },
          {
            name: 'Kathy Simon',
            description: 'Album cover for a country music band from Poland.',
            details: true,
            conception: false,
            type: 'Album cover',
            data: '2017',
            bac: 'rgba(55, 71, 83, .95)',
            img: "url('./src/assets/img/works/KathySimon/kathySimo_wide.png')",
            imgs: [
              {img: "./src/assets/img/works/KathySimon/KathySimon_EP_Wide.jpg"},
              {img: "./src/assets/img/works/KathySimon/KathySimon_EP_B_Wide.jpg"},
              {img: "./src/assets/img/works/KathySimon/KathySimon_EP_Wide.png"}
            ],
            modal: true,
            showModal: false
          },
          {
            name: 'Template site',
            description: 'A Vue.js web app for sale. This template is appropriate for small internet store or as a image based portfolio website. In process.',
            details: true,
            type: 'Website',
            bac: 'rgba(55, 71, 83, .95)',
            img: "url('./src/assets/img/works/template.png')",
            imgs: [
              {img: "./src/assets/img/works/template.png"}
            ],
            modal: true,
            showModal: false
          },
          {
            name: 'Hollow Quartet',
            description: 'A portfolio website for rock-folk band Hollow Quartet.',
            details: true,
            type: 'Website',
            link: 'http://hollowquartet.pl',
            bac: 'rgba(227, 181, 5, 0.95)',
            img: "url('./src/assets/img/works/HollowQuartet/hq.jpg')",
            imgs: [
              {img: "./src/assets/img/works/HollowQuartet/hq_1.jpg"},
              {img: "./src/assets/img/works/HollowQuartet/hq_2.jpg"}
            ],
            modal: true,
            showModal: false
          },
          {
            name: 'Marek Bracha',
            description: 'Portfolio website for polish classical pianist. Built with HTML5, CSS3 and simple JavaScript animations.',
            details: true,
            type: 'Website',
            link: 'http://marekbracha.pl',
            bac: 'rgba(227, 181, 5, 0.95)',
            img: "url('./src/assets/img/works/MarekBracha/marek.jpg')",
            imgs: [
              {img: "./src/assets/img/works/MarekBracha/mb_1.jpg"},
              {img: "./src/assets/img/works/MarekBracha/mb_2.jpg"}
            ],
            modal: true,
            showModal: false
          },
          {
            name: 'Posters',
            description: 'A set of poster I have made during last two years.',
            type: 'Print',
            bac: 'rgba(55, 71, 83, .95)',
            img: "url('./src/assets/img/works/Posters/hq_wide.jpg')",
            imgs: [
              {img: "./src/assets/img/works/Posters/hq_wide.jpg"},
              {img: "./src/assets/img/works/Posters/imuz_koncert.jpg"},
              {img: "./src/assets/img/works/Posters/wkm.jpg"},
              {img: "./src/assets/img/works/Posters/6Plyt.jpg"}
            ],
            modal: true,
            showModal: false
          }
        ]
      }
    }
  }
</script>
