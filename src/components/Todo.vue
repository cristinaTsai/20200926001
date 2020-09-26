<template>
  <div>
    <h1>Title</h1>
    <input v-model="text" />
    <button @click="add" :disabled="!text">Add</button>
    <ul>
      <li :class="{ grey: item.done }" 
      v-for="item in list" 
      :key="item.text">
        <input type="checkbox" v-model="item.done" />
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    text: "",
    list: [],
  }),
  methods: {
    add() {
      if (!this.text) return;
      const item = {
        text: this.text,
        done: false,
      };
      this.list.push(item);
      this.text = "";
    },
    remove(item) {
      const idx = this.list.indexOf(item);
      this.list.splice(idx, 1);
    },
  },
};
</script>

<style scoped>
.grey {
  color: #ddd;
}
.grey b{
    color: black;
}
</style>