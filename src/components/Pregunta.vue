<template>
    <div>
        <img src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif
 " alt="No se puede ver">
        <div class="pregunta-container">
            <input type="text" placeholder="Hazme una pregunta">
            <p>Recuerda terminar con el signo de interrogación (?)</p>

            <h2>Sere millonario?</h2>
            <h1>Yes, NO</h1>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>
img {
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