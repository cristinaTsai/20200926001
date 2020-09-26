<template>
  <div>
    <h1>{{text}}</h1>
    <img
      @load="imgLoaded"
      src="https://www.pamperedchef.com/iceberg/com/recipe/1125065-lg.jpg"
    />
  </div>
</template>

<script>
export default {
  data: () => ({
    text: 0,
  }),
  methods: {
    imgLoaded(event) {
      this.text = event.target.width;
    },
  },
};
</script>

<style scoped>
</style>