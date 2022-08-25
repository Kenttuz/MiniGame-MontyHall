<template>
    <div class="door-area">
        <!-- Moldura da Porta / coloca a classe selected apenas se estiver selecionada E não estiver aberta -->
        <div class="door-frame" :class="{ selected: selected && !open }">
            <!--Só vai exibir o presente se: -->
            <AllGift v-if="open && hasAllGift" />
        </div>
        <div class="door" :class="{ open }" @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <!-- Maçaneta da Porta -->
            <div class="knob" :class="{ selected }" @click="open = true"></div>
        </div>
    </div>
</template>

<script>
import AllGift from './AllGift.vue'

export default {
    name: 'AllDoor',
    components: { AllGift },
    //Aqui são passados como parâmetro para a porta
    props: {
        number: {},
        hasAllGift: { type: Boolean }
    },
    data: function () {
        //Aqui se refere a porta: (estado inicial dela)
        return {
            open: false,
            selected: false
        }
    }
}
</script>

<style scoped>
.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #aaa;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: 5px solid brown;
    border-top: 5px solid brown;
    border-right: 5px solid brown;

    display: flex;
    justify-content: center;
    /* Se refere aqui ao presente */
    align-items: flex-end;
}

.door {
    position: absolute;
    top: 4.7px;
    height: 295px;
    width: 170px;
    background-color: chocolate;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
}

.door .knob {
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background-color: brown;

    /* Aqui a maçaneta está se auto alinhando na direção do começo do flex */
    align-self: flex-start;
    margin-top: 60px;
}

.door-frame.selected {
    border-left: 5px solid yellow;
    border-top: 5px solid yellow;
    border-right: 5px solid yellow;
}

.door .knob.selected {
    background-color: yellow;
}

.door .number.selected {
    color: yellow;
}

.door.open {
    background-color: #0007;
}

.door.open .knob {
    display: none;
}

.door.open .number {
    display: none;
}
</style>
