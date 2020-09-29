<template>
  <div>
    <h1>Card</h1>
    <h2>{{ title }}</h2>
    <button @click="onClick">btn</button>
  </div>
</template>

<script>
export default {
  props: ["title"],
  methods: {
    onClick() {
      console.log("card click");
      this.$emit("clicked");
    },
  },
  //   computed:{
  //       myTitle(){
  //           return '-$this.-'
  //       }
  //   }
};
</script>

<style scoped>
</style>