<template>
  <v-container>
    <TodoInput @input="onInput" />
    <v-list>
      <v-list-item v-for="item in list" :key="item.text">
        <v-list-item-action>
          <v-checkbox v-model="item.done" />
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title :class="{'accent--text':item.done}">
            {{ item.text }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-container>
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
      };
      this.list.unshift(item);
    },
  },
};
</script>

