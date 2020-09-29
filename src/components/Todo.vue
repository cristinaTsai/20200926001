<template>
  <div>
    <TodoInput @input="onInput" />
    <ul id="list">
      <li :class="{ grey: item.done }" v-for="item in list" :key="item.text">
        <input type="checkbox" v-model="item.done" />
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
import TodoInput from "./TodoInput";

export default {
  components: { TodoInput },
  data: () => ({
    list: [],
  }),
  methods: {
    onInput(text) {
      const item = {
        text,
        done: false,
      }
      this.list.unshift(item)
    }
  },
};
</script>

<style scoped>
.grey {
  color: #ddd;
}
.red {
  color: red;
}
.grey b {
  color: black;
}
</style>