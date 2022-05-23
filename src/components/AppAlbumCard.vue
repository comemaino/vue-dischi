<template>
  <div class="col album-card text-center p-3">
    <img :src="disc.poster" alt="" />
    <h5 class="album-title mt-3">{{ disc.title }}</h5>
    <p class="artist mb-0">{{ disc.author }}</p>
    <p class="year">{{ disc.year }}</p>
  </div>
</template>

<script>
export default {
  name: "AppAlbumCard",
  props: {
    disc: Object,
  },
};
</script>

<style lang="scss" scoped>
.album-card {
  width: 19%;
  background-color: #0d0d0d;

  img {
    width: 100%;
  }

  h5 {
    font-size: 1rem;
    color: #fff;
    text-transform: uppercase;
  }

  p {
    font-size: 0.8rem;
    color: #999;
  }
}
</style>
