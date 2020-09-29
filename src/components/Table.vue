<template>

  <v-container>
    <TableInput @input="add" />
    <v-data-table :items="people" :headers="headers">
      <template #[`item.picture`]="{ value }">
        <v-avatar size="30">
          <v-img :src="value" />
        </v-avatar>
      </template>
    </v-data-table>
  </v-container>
</template>

<script>
import people from "../people.json";
import TableInput from "./TableInput";

export default {
    components:{
        TableInput,
    },
  data: () => ({
    people,
  }),
  computed: {
    headers() {
      return [
        { text: "Picture", value: "picture" },
        { text: "Name", value: "name" },
        { text: "Email", value: "email" },
        { text: "Gender", value: "gender" },
        { text: "Age", value: "age" },
      ];
    },
  },
  methods: {
    add(person) {
      this.people.unshift(person);
    },
  },
};
</script>