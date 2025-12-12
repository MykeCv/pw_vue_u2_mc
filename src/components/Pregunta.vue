<template>
    <div>
        <img v-if="imagen" :src="imagen" alt="No se puede ver" />
        <div class="pregunta-container">
            <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
            <p>Recuerda terminar con el signo de interrogación (?)</p>

            <h2>{{ pregunta }}</h2>
            <h1>{{ respuesta }}</h1>
        </div>
    </div>
</template>

<script>
import { consumirAPIFacade } from '../clients/YesNoClient.js';
export default {
    data() {
        return {
            pregunta: null,
            respuesta: null,
            imagen: null,
        };
    },
    watch: {
        pregunta(value, oldValue) {
            console.log(value);

            if (value.includes('?')) {
                //Llamar al API
                this.respuesta='Pensando...';
                this.consumir();
            }
        },
    },
    methods: {
        async consumir() {
            const resp = await consumirAPIFacade();
            console.log('Respuesta final');
            console.log(resp);
            console.log(resp.answer);
            this.respuesta = resp.answer;
            this.imagen = resp.image;
            console.log(this.imagen);
            
        },
    },
};
</script>

<style>
img{
    height: 100vh;
    width: 100vw;
    max-height: 100%;
    max-width: 100%;
    position: fixed;
    left: 0px;
    top: 0px;
}

.pregunta-container {
    position: relative;
    /* color: #ffffff; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

input {
    width: 300px;
    padding: 10px 15px;
    border-radius: 10px;
    border: none;

}

input:focus {
    outline: none;
    /*El outline le quita la sombra al imput */
}

h1,
h2,
p {
    color: white;
}

p {
    font-size: 20px;
}

h2 {
    margin-top: 150px;
}
</style>