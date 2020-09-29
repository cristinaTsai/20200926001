<template>
  <div>
    <input v-model="text" />
    <button @click="add" :disabled="invalid">Add</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    text: "",
  }),
  computed: {
    invalid() {
      return this.text.length <= 0 || this.text.length > 10;
    },
  },
  methods: {
    add() {
      if (this.invalid) return;
      this.$emit("input", this.text);
      this.text = "";
    },
  },
};
</script>

