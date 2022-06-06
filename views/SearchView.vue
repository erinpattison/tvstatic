<template>
  <div class="hero">
    <h2>Search TV Shows</h2>
    <label for="search" class="screenreader">Search TV Shows</label>
    <input
      id="search"
      type="text"
      placeholder="i.e. Game of Thrones"
      v-model="query"
    />
  </div>

  <main>
    <section class="searchresults">
      <Sidecard v-for="item in individualInfo" :key="item.show.id">
        <template #title>
          {{ item.show.name }}
        </template>

        <template #summary>
          <div class="summary">
            <p v-html="item.show.summary"></p>
          </div>
        </template>

        <template #image>
          <div v-if="item.show.image">
            <img :src="item.show.image.medium" class="showimage" />
          </div>
        </template>
      </Sidecard>
    </section>
  </main>
</template>

<script>
import Sidecard from "../components/Sidecard.vue";

export default {
  data() {
    return {
      rawData: [],
      query: "",
    };
  },
  components: {
    Sidecard: Sidecard,
  },
  methods: {
    fetchSearchAPI(query) {
      fetch(`https://api.tvmaze.com/search/shows?q=${query}`)
        .then((response) => {
          console.log("Response made");
          return response.json();
        })
        .then((jsonData) => {
          console.log("Data Received");
          console.log(jsonData);
          this.rawData = jsonData;
          return this.rawData;
        })
        .catch((err) => console.log(err.message));
    },
  },
  computed: {
    individualInfo: function () {
      const info = Object.keys(this.rawData).map((prop) => {
        return this.rawData[prop];
      });
      console.log("individualInfo returns: " + info);
      return info;
    },
  },
  created() {
    this.fetchSearchAPI(this.query);
  },
  watch: {
    query: function (query) {
      this.fetchSearchAPI(query);
    },
  },
};
</script>

<style scoped>
input {
  width: 35vw;
  height: 5vh;
  margin-right: 10px;
  font-size: 20px;
  color: var(--white);
  background-color: #0a0a0a;
  border: 2px solid var(--white);
  padding: 0 10px;
}
.summary {
  max-height: 280px;
  overflow-y: scroll;
}
.summary::-webkit-scrollbar {
  display: none;
}
.searchresults {
  display: flex;
  flex-wrap: wrap;
  margin-top: -5%;
}
.showimage {
  height: 20vw;
}
.screenreader {
  position: absolute;
  height: 1px;
  width: 1px;
  overflow: hidden;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
}
</style>
