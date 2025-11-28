<template>
  <div>
    <!--<ContadorView/>-->
    <DirectivasView />
  </div>
</template>

<script>
import ContadorView from "../src/views/ContadorView.vue";
import Contador from "./components/Contador.vue";
import DirectivasView from "./views/DirectivasView.vue";

export default {
  components: {
    ContadorView,
    Contador,
    DirectivasView,
  },
};
</script>

<style></style>