<template>
  <div id="app">
    <header>
      <AppHeader />
    </header>
    <main>
      <AppAlbumList />
    </main>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppAlbumList from "./components/AppAlbumList.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    AppAlbumList,
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
