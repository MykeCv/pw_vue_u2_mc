<template>
    <div class="pokemon-container">
        <img 
        :src="srcImagen" 
        alt="No se puede renderizar">
    </div>
</template>

<script>
export default {
    props: {
        pokemonId: {
            type: Number,
            required: true
        }
    },
    computed: {
        srcImagen() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
        }
    },
     /*Desmontaje de un componente*/
    beforeUnmount(){
        console.log("beforeUnmount: justo antes de que el componente se destruya.");
    },
    unmounted(){
        console.log("Unmounted: cuando fue el removido del DOM y destruido.");
    },
};
</script>


<style>
.pokemon-container {
    height: 200px;
}

img {
    position: relative;
    height: 200px;
    right: 1%;
}
</style>