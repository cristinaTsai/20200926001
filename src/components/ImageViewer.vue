<template>
  <div>
    <h1>{{imageWidth}} x {{imageHeight}}</h1>
    <img
      @load="imgLoaded"
      src="https://www.pamperedchef.com/iceberg/com/recipe/1125065-lg.jpg"
    />
  </div>
</template>

<script>
export default {
  data: () => ({
    imageWidth: 0,
    imageHeight:0,
  }),
  methods: {
    imgLoaded(event) {
      this.imageWidth = event.target.width;
      this.imageHeight = event.target.height;
    },
  },
};
</script>

<style scoped>
</style>