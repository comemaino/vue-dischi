<template>
  <div id="app">
    <header>
      <AppHeader :genresList="genres" @genreChanged="saveGenre($event)" />
    </header>
    <main>
      <AppAlbumList :discList="filteredDiscs" />
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppAlbumList from "./components/AppAlbumList.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    AppAlbumList,
  },

  data() {
    return {
      discs: [],
      genres: [],
      selectedGenre: "",
    };
  },

  computed: {
    filteredDiscs() {
      let filteredDiscs = [];
      if (this.selectedGenre === "") {
        filteredDiscs = this.discs;
      } else {
        filteredDiscs = this.discs.filter((item) => {
          return item.genre === this.selectedGenre;
        });
      }
      return filteredDiscs;
    },
  },

  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        console.log(resp);
        this.discs = resp.data.response;

        this.discs.forEach((item) => {
          if (!this.genres.includes(item.genre)) {
            this.genres.push(item.genre);
          }
        });
      });
  },
  methods: {
    saveGenre(newGenre) {
      this.selectedGenre = newGenre;
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";

main {
  height: calc(100vh - 60px);
  background-color: #222;
}
</style>
