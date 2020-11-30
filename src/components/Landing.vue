<template>
  <section>
    <div class="hero">
      <div class="col-md-10 ml-auto mr-auto">
        <form>
          <div class="input-group">
            <div class="input-group-prepend">
              <span class="input-group-text bg-white"><i class="fa fa-search" aria-hidden="true"></i></span>
            </div>
            <input type="text" v-model="searchQuery" v-on:keyup="africanImages()" class="form-control"
              placeholder="Search for photo" aria-describedby="search" required>
          </div>
        </form>
        <h2 v-if="searchQuery != ''" class="mb-0 mt-4">Search results for: "{{searchQuery}}"</h2>
      </div>
      <div class="col-md-8 mr-auto ml-auto hero-image-section">
        <div class="justify-content-center gallery">
          <div class="item-container pl-2 pr-2 pb-4" v-for="(human, index) in humans" :key="index">
            <img class="hero-image__img-wrap" @click="showModal = true, itemClicked(human)" :alt="userName"
              :src="human.urls.regular">
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">{{ human.user.name }}</h6>
              <small class="hero-image__role m-0 pl-2">{{ human.user.location }}</small>
            </div>
          </div>
        </div>
      </div>
      <div v-if="showModal" :human='human'>
        <transition name="modal">
          <div class="modal-mask">
            <div class="modal-wrapper">
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <div type="button" class="close text-white pr-0" @click="showModal=false">
                      <span aria-hidden="true">&times;</span>
                    </div>
                  </div>
                  <div class="img-container pb-4">
                    <img class="modal-img" @click="showModal = true" :alt="userName" :src="image">
                    <div class="modal__style text-left pt-3">
                      <h6 class="modal__name mb-0 text-left pl-4">{{ name }}</h6>
                      <small class="modal__role m-0 pl-4">{{ location }}</small>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'Landing',
    data() {
      return {
        showModal: false,
        image: '',
        name: '',
        location: '',
        humans: [],
        searchQuery: '',
        human: '',
      }
    },
    props: [
      'userName', 'userRole', 'userImg'
    ],
    methods: {
      itemClicked: function (human) {
        this.image = human.urls.regular;
        this.name = human.user.name;
        this.location = human.user.location;
      },
      africanImages() {
        this.axios.get(
            'https://api.unsplash.com/search/photos/?query=' + this.searchQuery +
            '&per_page=7&page=1&order_by=latest&client_id=zKonVXL1sV6nHsMPTpvGzQtC0wsNDHsTVoHpzjulbzs'
          )
          .then((response) => {
            this.humans = response.data.results
            let people = []
            for (let i = 0; i < this.humans.length; i++) {
              people = this.humans[i]
            }
            this.humans.push(people);
          })
      },
    },
    created() {
      this.searchQuery = 'african'
      this.africanImages();
      this.searchQuery = ''
    },
  }
</script>

<!--limits CSS to this component only -->
<style lang="scss">
  .close {
    font-size: 28px;
  }

  .modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, .5);
    display: table;
    transition: opacity .3s ease;
  }

  .modal-wrapper {
    display: table-cell;
    vertical-align: middle;
  }

  .gallery {
    margin-top: -3rem;
    display: grid;
    grid-auto-flow: dense;
    grid-template-columns: auto auto auto;
    width: 90%;
    position: relative;
    height: 100%;
    padding: 45px 0;
  }

  .item-container,
  .gallery {
    position: relative;
    height: 100%;
    width: 100%;
  }

  .item-container:first-child,
  .gallery {
    grid-column-start: span 1;
    grid-row-start: span 1;
  }

  .item-container:nth-child(2n+2),
  .gallery {
    grid-row-start: span 2;
  }

  .hero {
    background-color: #F0F0F0;
    height: 18rem;
    padding: 6.5rem 0;
  }

  input[type="text"] {
    outline: none;
    box-shadow: none !important;
    border: 0;
    height: 3.5rem;
  }

  .input-group-text {
    border: 0 !important;
    height: 3.5rem;
  }

  .hero-image__img-wrap:hover {
    transform: scale(1.025);
  }

  .hero-image__img-wrap {
    width: 100%;
    height: 100%;
    background-color: #E8E8E8;
    border-radius: 4px;
    object-fit: cover;
    box-shadow: 0 0 16px #333;
    transition: all 1.5s ease;
    transition: grid-row-start 300ms linear;
    transition: transform 300ms ease;
    cursor: pointer;
  }

  .modal-img {
    width: 100%;
    height: 60vh;
    background-color: #E8E8E8;
    border-radius: 4px;
    object-fit: cover;
    cursor: pointer;
  }

  .modal__name {
    margin-bottom: 0.5rem;
    color: blue($color: #3e5cbe);
    font-size: 1.1rem;
  }

  .modal__role {
    color: blue($color: #3e5cbe);
    font-size: 1rem;
  }

  .hero-image__role {
    color: #ffffff;
    font-size: 1rem;
  }

  .hero-image__style {
    margin-top: -5rem;
  }

  .hero-image__name {
    margin-bottom: 0.5rem;
    color: #ffffff;
    font-size: 1.1rem;
  }

  .hero-image-section {
    padding-top: 3rem;
  }

  .modal-content {
    background-color: transparent !important;
    border: 0 !important;
  }

  .img-container {
    background-color: #F0F0F0;
    border-radius: 4px;
  }
</style>