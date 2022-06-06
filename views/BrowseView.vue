<template>
  <div class="hero">
    <h2>Browse</h2>
  </div>

  <section class="browse">
    <div class="browseitem" v-for="item in myApiInfo" :key="item.id">
      <img :src="item.image.thumbnail" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      apiData: [],
      id: undefined,
    };
  },
  methods: {
    myOwnApi() {
      fetch(`https://erinpattison-tv-api.herokuapp.com/shows`)
        .then((response) => {
          console.log("Response made");
          console.log(response);
          return response.json();
        })
        .then((jsonData) => {
          console.log("Data Received");
          console.log(jsonData);
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
.browse {
  padding: 20px;
  display: flex;
  flex-wrap: wrap;
}
.browseitem {
  width: 15vw;
  margin: 10px;
  border-radius: 5px;
  transition: 0.1s linear;
}
.browseitem:hover {
  transform: scale(1.1);
}
.browseitem img {
  width: 102%;
}
</style>
