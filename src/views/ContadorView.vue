<template>
  <div>
    <Contador tit="Contador1" :inicio="4+4"/>
    <Contador tit="Contador2" :inicio="10"/>
  </div>
</template>

<script>
import Contador from "../components/Contador.vue";
export default {
  components: {
    Contador,
  },
};
</script>

<style>
</style>