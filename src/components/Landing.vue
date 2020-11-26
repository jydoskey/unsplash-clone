<template>
  <section>
    <div class="hero">
      <div class="col-md-10 ml-auto mr-auto">
        <form>
          <div class="input-group">
            <div class="input-group-prepend">
              <span class="input-group-text bg-white"><i class="fa fa-search" aria-hidden="true"></i></span>
            </div>
            <input type="text" class="form-control" placeholder="Search for photo" aria-describedby="search" required>
          </div>
        </form>
      </div>
      <div class="col-md-7 mr-auto ml-auto hero-image-section">
        <div class="justify-content-center gallery">
          <div class="item-container pl-2 pr-2 pb-4" v-for="(human, index) in humans" :key="index">
            <img class="hero-image__img-wrap" :alt="userName" :src="human.img">
            <div class="hero-image__style">
              <h6 class="hero-image__name mb-0">{{ human.name }}</h6>
              <small class="hero-image__role m-0">{{ human.role }}</small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'Landing',
    props: [
      'userName', 'userRole', 'userImg'
    ],
    data() {
      return {
        humans: [{
            name: 'JR Kanu',
            role: 'CEO & Founder',
            img: 'https://source.unsplash.com/random/?african,fun'
          },
          {
            name: 'Tunde Akiode',
            role: 'Chief Retail Officer',
            img: 'https://source.unsplash.com/random/?african,food'
          },
          {
            name: 'Boyewa Adepoju',
            role: 'Product Marketer',
            img: 'https://source.unsplash.com/random/?african,dance'
          },
          {
            name: 'Adedamola Adeniran',
            role: 'Engineering Manager',
            img: 'https://source.unsplash.com/random/?african,party'
          },
          {
            name: 'Abuoma Nwadike',
            role: 'Product Manager',
            img: 'https://source.unsplash.com/random/?african,smile'
          },
          {
            name: 'Toye Iwakin',
            role: 'Software Engineer',
            img: 'https://source.unsplash.com/random/?african,travel'
          },
          {
            name: 'Jide Omotola',
            role: 'Software Engineer',
            img: 'https://source.unsplash.com/random/?african,farm'
          }
        ]
      }
    },
  }
</script>

<!--limits CSS to this component only -->
<style lang="scss">
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
    padding: 7.5rem 0;
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

  .hero-image__role {
    color: #ffffff;
    font-size: 1rem;
  }

  .hero-image__style {
    margin-top: -3.5rem;
  }

  .hero-image__name {
    margin-bottom: 0.5rem;
    color: #ffffff;
    font-size: 1.1rem;
  }

  .hero-image-section {
    padding-top: 4.5rem;
  }
</style>