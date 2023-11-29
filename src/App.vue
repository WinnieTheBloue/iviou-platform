<script>
import Nav from "./components/Nav.vue";
export default {
  components: {
    Nav,
  },
};
</script>

<template>
  <router-view />
   <Nav />
</template>

<style scoped></style>
