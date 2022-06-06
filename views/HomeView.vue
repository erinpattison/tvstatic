<template>
  <div class="hero">
    <h2>TV Static</h2>
  </div>

  <section class="collection top">
    <h2>Curated Collection: Drama</h2>
    <Swiper
      class="swiper"
      :modules="modules"
      :slides-per-view="6"
      :space-between="2"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
    >
      <swiperSlide>
        <img :src="myApiInfo[51].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[65].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[67].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[89].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[94].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[121].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[136].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[145].image.thumbnail" class="swiperimg" />
      </swiperSlide>
    </Swiper>
  </section>

  <section class="collection">
    <h2>Curated Collection: Comedy</h2>
    <Swiper
      class="swiper"
      :modules="modules"
      :slides-per-view="6"
      :space-between="2"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
    >
      <swiperSlide>
        <img :src="myApiInfo[134].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[135].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[142].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[164].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[175].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[50].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[39].image.thumbnail" class="swiperimg" />
      </swiperSlide>
    </Swiper>
  </section>

  <section class="collection">
    <h2>Curated Collection: Horror</h2>
    <Swiper
      class="swiper"
      :modules="modules"
      :slides-per-view="6"
      :space-between="2"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
    >
      <swiperSlide>
        <img :src="myApiInfo[103].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[158].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[160].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[7].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[4].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[24].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[100].image.thumbnail" class="swiperimg" />
      </swiperSlide>
      <swiperSlide>
        <img :src="myApiInfo[101].image.thumbnail" class="swiperimg" />
      </swiperSlide>
    </Swiper>
  </section>

  <!-- {{apiData}} -->
</template>

<script>
import { Navigation, Pagination, Scrollbar, A11y } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "swiper/css/scrollbar";

export default {
  data() {
    return {
      apiData: [],
      id: undefined,
    };
  },
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const onSwiper = (swiper) => {};
    const onSlideChange = () => {};
    return {
      onSwiper,
      onSlideChange,
    };
  },
  methods: {
    myOwnApi() {
      fetch(`https://erinpattison-tv-api.herokuapp.com/shows`)
        .then((response) => {
          console.log("Response made");
          return response.json();
        })
        .then((jsonData) => {
          console.log("Data Received");
          this.apiData = jsonData;
          return this.apiData;
        })
        .catch((err) => console.log(err.message));
    },
  },
  computed: {
    myApiInfo: function () {
      const info = Object.keys(this.apiData).map((prop) => {
        return this.apiData[prop];
      });
      return info;
    },
  },
  created() {
    this.myOwnApi();
  },
};
</script>

<style scoped>
main {
  margin-top: -10%;
}
.collection {
  padding: 10px;
}
.collection h2 {
  color: var(--white);
  font-size: 2vw;
  text-shadow: 3px 3px 4px #0a0a0a;
}

.top {
  margin-top: -10%;
}
.swiper {
  overflow: visible;
}
.swiperimg {
  max-width: 15vw;
  border-radius: 10px;
  box-shadow: 2px 2px 5px #0a0a0a;
  transition: 0.1s linear;
}
.swiperimg:hover {
  box-shadow: 4px 4px 10px #0a0a0a;
  transform: scale(1.1);
}
.flex {
  display: flex;
}
</style>
