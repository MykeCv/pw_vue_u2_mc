<template>
    <h1 v-if="ganador">Correcto! Ganaste</h1>
    <h1 v-if="perdedor">Incorrecto! Vuelve a intentarlo</h1>
    <button @click="destruir()">Destruir</button>
    <PokemonImagen v-if="mostrar" :pokemonId="pokemonGanador" />
    <PokemonOpciones @seleccionado="evaluarGanador($event)" :listaPokemons="pokemonArr" />
</template>
    
<script>
import PokemonImagen from '../components/PokemonImagen.vue'
import PokemonOpciones from '../components/PokemonOpciones.vue'
import { obtenerVectorPokemonFachada, obtenerAleatorioFachada } from "../clients/PokemonClient"

export default {
    components: {
        PokemonImagen,
        PokemonOpciones,
    },
    data() {
        return {
            pokemonArr: [],
            pokemonGanador: null,
            ganador: false,
            perdedor: false,
            mostrar: true,
        };
    },
    /*Cuando se crea el Componente*/
    beforeCreate() {
        console.log("beforeCreate: apenas inicia la instancia del componente");
    },
    created() {
        console.log("create: cuando ya han pasado cuando se resolvieron data, computed, methods, watch");
    },
    /*Cuando se Monta el componente: se renderiza o visualiza el componente*/
    beforeMount(){
        console.log("beforeMount: justo antes del primer render de un elemento HTML");
    },
    mounted() {
        console.log('Componente montado: cuando el componente ya se renderizo');
        this.iniciarJuego();
    },

    /*Actualización de un Componente*/
    beforeUpdate(){
        console.log("beforeUpdate: cuando cambío un data/props y Vue esta por re-renderizar.");
    },
    updated(){
        console.log("updated: cuando ya se actualizo tras el re-renderización");
    },
   
    methods: {
        async iniciarJuego() {
            this.pokemonArr = await obtenerVectorPokemonFachada();

            const idAleatorio = obtenerAleatorioFachada(0, 3);
            this.pokemonGanador = this.pokemonArr[idAleatorio].id;
        },
        evaluarGanador(idGanador) {
            console.log('Valor recibido desde padre');
            console.log(idGanador);
            if (idGanador === this.pokemonGanador) {
                console.log('Ganador');
                this.ganador = true;
                return;
            } else {
                console.log('Perdedor');
                this.perdedor = true;
                return;
            }
        },
        destruir(){
            this.mostrar = false;
        }
    },
};
</script>

<style></style>