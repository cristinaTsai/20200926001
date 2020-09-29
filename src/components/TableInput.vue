<template>
  <v-dialog v-model="dialog">
    <template #activator="{ on, attrs }">
      <v-btn v-bind="attrs" v-on="on">New</v-btn>
    </template>
    <v-card>
      <v-card-text>
        <v-form @submit.prevent="submit">
          <v-text-field v-model="name" label="Name" />
          <v-text-field v-model="email" label="Email" />
          <v-radio-group v-model="gender" label="Gender">
            <v-radio value="male" label="Male" />
            <v-radio value="female" label="Female" />
          </v-radio-group>
          <v-text-field v-model.number="age" label="Age" />
          <v-btn type="submit">Add</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data: () => ({
    name: "",
    email: "",
    gender: "female",
    age: "",
    dialog :false,
  }),
  methods: {
    submit() {
      const person = {
        name: this.name,
        email: this.email,
        gender: this.gender,
        age: this.age,
      };
      this.$emit("input", person);
      this.dialog = false;
    },
  },
};
</script>