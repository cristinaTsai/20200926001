<template>
<Todo/>
  <!-- <div>
    <Card title="test" @click="cardClick" />
    <Card title="result"  />
  </div> -->
</template>

<script>
import Todo from "./components/Todo.vue";

export default {
  name: "App",
  components: {
    Todo,
  },
  methods: {
    cardClick() {
      console.log("card click in app");
    },
  },
};
</script>

