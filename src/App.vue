<!-- Parte do HTML -->
<template>
    <div id="app">
        <h1>Problema de MontyHall</h1>
        <!-- Os : em hasAllGift é porque ele vai retornar um tipo Boolean -->
        <div class="form">
            <!-- Só vai aparecer essa div quando não estiver startado -->
            <div v-if="!started">
                <label for="portsAmount">Quantas portas?</label>
                <input
                    type="text"
                    id="portsAmount"
                    sizer="3"
                    v-model.number="portsAmount"
                />
            </div>
            <div v-if="!started">
                <label for="selectedPort">Qual porta é a premiada?</label>
                <input
                    type="text"
                    id="selectedPort"
                    sizer="3"
                    v-model.number="selectedPort"
                />
            </div>
            <button v-if="!started" @click="started = true">INICIAR</button>
            <button v-if="started" @click="started = false">Reiniciar</button>
        </div>

        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <AllDoor :hasAllGift="i == selectedPort" :number="i"></AllDoor>
            </div>
        </div>
    </div>
</template>

<script>
import AllDoor from './components/AllDoor.vue'

export default {
    name: 'App',
    components: { AllDoor },
    data: function () {
        return {
            started: false,
            portsAmount: 3,
            selectedPort: null
        }
    }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
}

Body {
    color: white;
    background: linear-gradient(to right, #3494e6, #ec6ead);
}

#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    border: 1px solid black;
    background-color: #0004;
    padding: 20px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form,
.form input,
.form.button {
    margin-bottom: 20px;
    margin-left: 10px;
    font-size: 1.7rem;
}

button {
    font-weight: bold;

    width: 80px;
    height: 30px;
    background: white;
    color: black;
    cursor: pointer;

    border: 2px solid black;
    border-radius: 10px;
}

button:hover {
    background: black;
    color: white;

    border: 2px solid white;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;

    /* QUEBRAR AS LINHAS */
    flex-wrap: wrap;
}
</style>
