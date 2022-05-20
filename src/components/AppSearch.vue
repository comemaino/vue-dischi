<template>
  <select
    class="m-4"
    name="genres"
    id="genres"
    v-model="selectedOption"
    @change="$emit('selection', selectedOption)"
  >
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
  </select>
</template>

<script>
export default {
  name: "AppSearch",
  data() {
    return {
      selectedOption: "",
    };
  },

  methods: {},
};
</script>

<style lang="scss" scoped></style>
