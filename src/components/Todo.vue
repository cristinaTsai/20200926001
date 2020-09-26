<template>
  <div>
    <input v-model="text" />
    <button @click="add" :disabled="!text">Add</button>
    <ul>
      <li v-for="item in list" :key="item.text">
        <input type="checkbox" v-model="item.done" />
        {{ item.text }}
      </li>
    </ul>
    <pre>
        {{ JSON.stringify(list, null, 2) }}
    </pre>
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
</style>