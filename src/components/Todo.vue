<template>
  <div>
    <input v-model="text" />
    <button @click="add" :disabled ="!text">
        Add
    </button>
    <ul>
      <li v-for="item in list" :key="item">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    text: "",
    list: ["a", "b", "c"],
  }),
  methods: {
    add() {
        if(!this.text) return
        this.list.push(this.text)
        this.text = "";
    },
  },
};
</script>

<style scoped>
</style>