<template>
  <div class="container d-flex p-3">
    <div calss="wrapper d-flex">
      <div class="container"></div>
      <div class="row row-cols-5 justify-content-between g-3">
        <AppAlbumCard
          v-for="(discItem, index) in discList"
          :key="index"
          :disc="discItem"
        />
      </div>
    </div>
  </div>
</template>

<script>
import AppAlbumCard from "./AppAlbumCard.vue";

export default {
  name: "AppAlbumList",
  components: {
    AppAlbumCard,
  },

  props: {
    discList: Array,
  },

  // data() {
  //   return {
  //     albums: [],
  //     selectedOption: "",
  //   };
  // },

  // computed: {
  //   albumFilter() {
  //     const filteredAlbums = this.albums.filter((item) => {
  //       return item.genre.includes(this.selectedOption);
  //     });
  //     return filteredAlbums;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
.container {
  align-items: center;
  height: 100%;
}
</style>
