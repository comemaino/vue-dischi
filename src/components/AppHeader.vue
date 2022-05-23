<template>
  <div class="header">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Spotify_App_Logo.svg/400px-Spotify_App_Logo.svg.png"
      alt=""
    />

    <select
      class="m-4"
      name="genres"
      id="genres"
      @change="$emit('genreChanged', selectedGenre)"
      v-model="selectedGenre"
    >
      <option value="">Genres</option>
      <option v-for="(item, index) in genresList" :key="index" :value="item">
        {{ item }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "AppHeader",

  props: {
    genresList: Array,
  },

  data() {
    return {
      selectedGenre: "",
    };
  },
};
</script>

<style lang="scss" scoped>
.header {
  background-color: #0d0d0d;

  img {
    height: 60px;
  }
}
</style>
