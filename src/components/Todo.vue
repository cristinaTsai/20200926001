<template>
  <div>
    <input v-model="text" />
    <button @click="add" :disabled="!text" :class="{ grey: invalid }" >Add</button>
    <br />
    <!-- <h2 :class="{ red: textLength > 10 }"> -->
    <h2 :class="{ red: invalid }">
      {{ textLength }}
    </h2>
    <ul id="list">
      <li :class="{ grey: item.done }" v-for="item in list" :key="item.text">
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
  computed: {
    textLength() {
      return this.text.length;
    },
    invalid() {
      return this.text.length <= 0 || this.text.length >10;
    },
  },
  methods: {
    add() {
      if (!this.text) return;
      if (this.invalid) return;
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
.red {
  color: red;
}
.grey b {
  color: black;
}
</style>