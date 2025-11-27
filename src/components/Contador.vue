<template>
  <div>
    <h1>{{ titulo }}</h1>

    <p>{{ numero }} <sup>2</sup>= {{ calcularCuadrado }}</p>

    <p>{{ numero }} <sup>2</sup>= {{ calcularCuadrado }}</p>

    <p>{{ numero }} <sup>2</sup>= {{ calcularCuadrado }}</p>

    <p>{{ numero }} <sup>2</sup>= {{ calcularCubo }}</p>

    <p>{{ numero }} <sup>2</sup>= {{ obtenerCubo() }}</p>
    <div>
      <button v-on:click="incrementar()">+1</button>
      <button v-on:click="decrementar()">-1</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: this.inicio,
      titulo: "Contador",
    };
  },
  methods: {
    obtenerCuadrado() {
      console.log("Entro a obtener cuadrado");
      return this.numero * this.numero;
    },
    obtenerCubo() {
      return this.numero * this.numero * this.numero;
    },
    incrementar() {
        console.log(this.tit);
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  computed: {
    calcularCuadrado() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero;
    },
    calcularCubo() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero * this.numero;
    },
  },
  props:['tit',"inicio"],
};
</script>
<style>
</style>