<template>
  <div>
    <ContadorView />
  </div>
</template>

<script>
import ContadorView from "../src/views/ContadorView.vue";
import Contador from "./components/Contador.vue";
export default {
  components: {
    ContadorView,
    Contador,
  },
};
</script>

<style>
</style>