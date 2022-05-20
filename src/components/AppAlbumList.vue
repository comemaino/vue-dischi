<template>
  <div class="container d-flex p-3">
    <div class="container" v-if="loading">
      <AppLoading />
    </div>
    <div calss="wrapper d-flex" v-else>
      <div class="container">
        <AppSearch @selection="saveSelection($event)" />
      </div>
      <div class="row row-cols-5 justify-content-between g-3">
        <AppAlbumCard
          v-for="(item, index) in albumFilter"
          :key="index"
          :album="item"
        />
      </div>
    </div>
  </div>
</template>

<script>
import AppAlbumCard from "./AppAlbumCard.vue";
import AppSearch from "./AppSearch.vue";
import AppLoading from "./AppLoading.vue";
import axios from "axios";

export default {
  name: "AppAlbumList",
  components: {
    AppAlbumCard,
    AppLoading,
    AppSearch,
  },

  data() {
    return {
      albums: [],
      loading: true,
      selectedOption: "",
    };
  },

  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.albums = resp.data.response;
        this.loading = false;
        console.log(this.albums);
      });
  },

  computed: {
    albumFilter() {
      const filteredAlbums = this.albums.filter((item) => {
        return item.name.includes(this.selectedOption);
      });
      return filteredAlbums;
    },
  },

  methods: {
    saveSelection(selection) {
      this.selectedOption = selection;
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  align-items: center;
  height: 100%;
}
</style>
