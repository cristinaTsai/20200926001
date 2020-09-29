<template>
  <v-form @submit.prevent="add">
    <v-container>
      <v-row>
        <v-col cols="9">
          <v-text-field v-model="text" />
          <!-- <v-text-field v-model="text" @keydown.enter="add"/> -->
        </v-col>
        <v-col cols="3">
          <v-btn type="submit" :disabled="invalid">Add</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
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

