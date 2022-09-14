<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonOne text="Add Task" color="Green" />
  </header>
</template>

<script>
import ButtonOne from "./ButtonOne.vue";
export default {
  name: "HeaderOne",
  props: {
    title: String,
  },
  components: {
    ButtonOne,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
