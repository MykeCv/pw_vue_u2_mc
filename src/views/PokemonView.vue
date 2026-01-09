<template>
    <h1 v-if="ganador">Correcto! Ganaste</h1>
    <h1 v-if="perdedor">Incorrecto! Vuelve a intentarlo</h1>
    <PokemonImagen :pokemonId="pokemonGanador"/>
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
        };
    },
    mounted() {
        console.log('Componente montado');
        this.iniciarJuego();
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
            if(idGanador === this.pokemonGanador){
                console.log('Ganador');
                this.ganador = true;
                return;
            }else{
                console.log('Perdedor');
                this.perdedor = true;
                return;
            }
        }
    },
};
</script>

<style></style>