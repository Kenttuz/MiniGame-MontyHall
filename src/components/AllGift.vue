<template>
    <div class="gift">
        <div class="gift-tie-1">{{ msg }}</div>
        <div class="gift-tie-2">{{ msg }}</div>
        <div class="gift-top">{{ msg }}</div>
        <div class="gift-body">{{ msg }}</div>
    </div>
</template>

<script>
export default {
    name: 'AllGift'
}
</script>

<!-- Adicione o atributo "scoped" para limitar o CSS apenas a este componente  -->
<style scoped>
.gift {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 10;
}

/* Tampa do presente */
.gift-top {
    width: 100px;
    height: 25px;
    background-color: #7aa944;
}

/* Corpo do presente */
.gift-body {
    width: 90px;
    height: 60px;
    background-color: #5c7e32;
}

/* Laço Vertical do presente */
.gift-tie-1 {
    position: absolute;
    width: 15px;
    height: 85px;
    background-color: red;
}

/* Laço Horizontal do presente */
.gift-tie-2 {
    position: absolute;
    top: 40px;
    width: 90px;
    height: 15px;
    background-color: red;
}
</style>
