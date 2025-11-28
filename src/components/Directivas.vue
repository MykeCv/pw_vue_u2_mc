<template>
    <div>
        <label for="id_nombre">Nombre: </label>
        <input v-model="nombre" id="id_nombre" type="text">
        <br>
        <!--<p>{{ nombre }}</p>-->

        <label for="id_apellido">Apellido: </label>
        <input v-model="apellido" id="id_apellido" type="text">

        <button v-on:click="imprimirNombre()">Imprimir Nombre</button>
        <button v-on:click="agregarEstudiante()">Agregar Estudiante</button>
        <!--<h1>{{ arreglo[0] }}</h1>-->

        <ul>
            <!--<li v-show="nombre" v-for="{ nombre, apellido } in arreglo" :key="nombre">
                {{ nombre }} {{ apellido }}</li>-->
        </ul>
        <h2>Ahora tabla</h2>
            <table border="1">
                <th>Nombre</th>
                <th>Apellido</th>
                <tr v-show="nombre || apellido" v-for="{nombre, apellido} in arreglo" :key="nombre">
                    <td>{{ nombre }}</td>
                    <td>{{ apellido }}</td>
                </tr>
                

            </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nombre: null,
            apellido: null,
            arreglo: [],
        }
    },
    methods: {
        imprimirNombre() {
            console.log(this.nombre);
        },
        agregarEstudiante() {
            const estu = {
                nombre: this.nombre,
                apellido: this.apellido,
            };
            console.log("Se agrega Estudiante");
            console.log(estu);
            this.arreglo.push(estu);
            this.limpiarFomulario();
        },
        limpiarFomulario() {
            this.nombre = null;
            this.apellido = null;
        },
    },
};
</script>

<style>
table{
    font-size: 25px;
}
</style>