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
      <div class="col-md-8 mr-auto ml-auto hero-image-section">
        <div class="row text-center justify-content-center">
          <div class="col-lg-3 col-md-4 col-6 " v-for="human in humans" :key="human.name">
            <div class="hero-image-style">
              <div class="hero-image pr-1 pl-1">
                <div class="hero-image__img-wrap">
                  <div class="hero-image__img" :alt="userName"
                    v-bind:style="{ backgroundImage: `url(${human.img})` }">
                  </div>
                </div>
                <div class="hero-image__style">
                  <h6 class="hero-image__name">{{ human.name }}</h6>
                  <small class="hero-image__role m-0">{{ human.role }}</small>
                </div>
              </div>
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
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/JRKanu.CEO&Founder.jpg'
          },
          {
            name: 'Tunde Akiode',
            role: 'Chief Retail Officer',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/TundeAkiode.ChiefRetailOfficer.jpg'
          },
          {
            name: 'Boyewa Adepoju',
            role: 'Product Marketer',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/BoyewaAbiodun-Adepoju.HeadofMarketung&Communications.jpg'
          },
          {
            name: 'Adedamola Adeniran',
            role: 'Engineering Manager',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/adedamola-adeniran.jpg'
          },
          {
            name: 'Abuoma Nwadike',
            role: 'Product Manager',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/AbuomaNwadike.ProductManager.jpg'
          },
          {
            name: 'Toye Iwakin',
            role: 'Software Engineer',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/ToyeIwakin.Softwareengineer.jpg'
          },
          {
            name: 'Jide Omotola',
            role: 'Software Engineer',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/OlajideOmotola.softwaredeveloper.jpg'
          },
          {
            name: 'Eunice Bakare',
            role: 'Software Engineer',
            img: 'https://storage.googleapis.com/moneyme-mybank/web/team/BakareEunice.androiddeveloper.jpg'
          },
        ]
      }
    },
  }
</script>

<!--limits CSS to this component only -->
<style lang="scss">
  .hero {
    background-color: #F0F0F0;
    height: 18rem;
    padding: 7.5rem 0;
  }

  input[type="text"] {
    outline: none;
    box-shadow: none !important;
    border: 0;
    height: 3rem;
  }

  .input-group-text {
    border: 0 !important;
    height: 3rem;
  }

  .hero-image {
    display: block;

    &:hover,
    &:focus {
      .hero-image__img-wrap {
        filter: none;
      }
    }
  }



  .hero-image__img-wrap {
    margin: 0 auto;
    transition: .5s ease;
    width: 35.53vw;
    height: 35.53vw;
    border-radius: 50%;

    @media (min-width: 768px) {
      width: 20vw;
      height: 20vw;
    }

    @media (min-width: 992px) {
      width: 17vw;
      height: 17vw;
    }

    @media (min-width: 1200px) {
      width: 15vw;
      height: 15vw;
    }
  }

  .hero-image__img {
    display: block;
    width: 100%;
    height: 100%;
    background-position: top;
    background-repeat: no-repeat;
    background-size: cover;
    background-color: grey;
    border-radius: 4px;
  }

  .hero-image__role {
    color: rgb(229, 226, 226);

    @media (min-width:320px) {
      font-size: 1rem;

    }

    @media (min-width: 768px) {
      font-size: 1.125rem;
    }

    @media (min-width: 1200px) {
      font-size: 1.25rem;
    }
  }

  .hero-image__style {
    padding: 1rem 0.2rem;

    @media (min-width: 992px) {
      padding: 2rem 0.5rem;
    }
  }

  .hero-image__name {
    margin-bottom: 0.5rem;
    color: #ffffff;

    @media (min-width:320px) {
      font-size: 1rem;

    }

    @media (min-width: 768px) {
      font-size: 1.125rem;
    }

    @media (min-width: 1200px) {
      font-size: 1.25rem;
    }
  }

  .hero-image-style {
    margin-bottom: 2.5rem;

    @media (min-width: 768px) {
      margin-bottom: 5rem;
    }
  }

  .hero-image-section {
    padding-top: 4.5rem;
  }
</style>