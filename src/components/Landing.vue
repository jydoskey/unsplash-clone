<template>
  <section>
    <div class="hero">
      <div class="col-md-10 ml-auto mr-auto">
        <form>
          <div class="input-group">
            <div class="input-group-prepend">
              <span class="input-group-text bg-white"
                ><i class="fa fa-search" aria-hidden="true"></i
              ></span>
            </div>
            <input
              type="text"
              v-model="searchQuery"
              v-on:keyup="africanImages()"
              class="form-control"
              placeholder="Search for photo"
              aria-describedby="search"
              required
            />
          </div>
        </form>
        <h2 v-if="searchQuery != ''" class="mb-0 mt-4">
          Search results for: "{{ searchQuery }}"
        </h2>
      </div>
      <div class="masonry-wrapper">
        <div class="masonry hero-image-section">
          <div class="masonry-item">
            <img
              :src="humans[0].urls.regular"
              @click="(showModal = true), itemClicked(humans[0])"
              style="width: 100%; height: 325px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[0].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[0].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[1].urls.regular"
              @click="(showModal = true), itemClicked(humans[1])"
              style="width: 100%; height: 450px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[1].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[1].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[2].urls.regular"
              @click="(showModal = true), itemClicked(humans[2])"
              style="width: 100%; height: 280px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[2].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[2].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[3].urls.regular"
              @click="(showModal = true), itemClicked(humans[3])"
              style="width: 100%; height: 540px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[3].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[3].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[4].urls.regular"
              @click="(showModal = true), itemClicked(humans[4])"
              style="width: 100%; height: 380px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[4].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[4].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[5].urls.regular"
              @click="(showModal = true), itemClicked(humans[5])"
              style="width: 100%; height: 300px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[5].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[5].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[6].urls.regular"
              @click="(showModal = true), itemClicked(humans[6])"
              style="width: 100%; height: 400px"
              :alt="userName"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[6].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[6].user.location
              }}</small>
            </div>
          </div>
          <div class="masonry-item">
            <img
              :src="humans[7].urls.regular"
              @click="(showModal = true), itemClicked(humans[7])"
              :alt="userName"
              style="width: 100%; height: 300px"
              class="masonry-content"
            />
            <div class="hero-image__style text-left">
              <h6 class="hero-image__name mb-0 pl-2">
                {{ humans[7].user.name }}
              </h6>
              <small class="hero-image__role m-0 pl-2">{{
                humans[7].user.location
              }}</small>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showModal" :human="human">
        <transition name="modal">
          <div class="modal-mask">
            <div class="modal-wrapper">
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <div
                      type="button"
                      class="close text-white pr-0"
                      @click="showModal = false"
                    >
                      <span aria-hidden="true">&times;</span>
                    </div>
                  </div>
                  <div class="img-container pb-4">
                    <img class="modal-img" :alt="userName" :src="image" />
                    <div class="modal__style text-left pt-3">
                      <h6 class="modal__name mb-0 text-left pl-4">
                        {{ name }}
                      </h6>
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
  name: "Landing",
  data() {
    return {
      showModal: false,
      image: "",
      name: "",
      location: "",
      humans: [],
      searchQuery: "",
      human: "",
    };
  },
  props: ["userName", "userRole", "userImg"],
  methods: {
    defaultSearch() {
      if (this.searchQuery == '') {
            this.searchQuery = 'african'
          }
    },
    itemClicked: function (human) {
      this.image = human.urls.regular;
      this.name = human.user.name;
      this.location = human.user.location;
    },
    africanImages() {
      let search_query = this.searchQuery;
      this.axios.get(
          "https://api.unsplash.com/search/photos/?query=" +
            search_query +
            "&per_page=7&page=1&order_by=latest&client_id=zKonVXL1sV6nHsMPTpvGzQtC0wsNDHsTVoHpzjulbzs"
        )
        .then((response) => {
          this.humans = response.data.results;
          let people = [];
          for (let i = 0; i < this.humans.length; i++) {
            people = this.humans[i];
          }
          this.humans.push(people);
        });
    },
  },
  created() {
    this.defaultSearch()
    this.africanImages();
    this.searchQuery = ''
  },
};
</script>