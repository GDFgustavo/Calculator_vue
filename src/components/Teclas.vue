<script setup>
const props = defineProps(['limpaDisplay', 'valorTeclas', 'calcular'])
</script>
<template>
    <div class="calculator-teclas"> <!--Adicionando as teclas-->
        <button @click="props.limpaDisplay('C')" class="btn rounded-5 border-none m-2 p-3 colorbutton --red">C</button>
        <button @click="props.valorTeclas('%')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">%</button>
        <button @click="props.valorTeclas('/')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">÷</button>
        <button @click="props.valorTeclas('*')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">x</button>
        <button @click="props.valorTeclas('7')" class="btn rounded-5 border-none m-2 p-3 colorbutton">7</button>
        <button @click="props.valorTeclas('8')" class="btn rounded-5 border-none m-2 p-3 colorbutton">8</button>
        <button @click="props.valorTeclas('9')" class="btn rounded-5 border-none m-2 p-3 colorbutton">9</button>
        <button @click="props.valorTeclas('-')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">-</button>
        <button @click="props.valorTeclas('4')" class="btn rounded-5 border-none m-2 p-3 colorbutton">4</button>
        <button @click="props.valorTeclas('5')" class="btn rounded-5 border-none m-2 p-3 colorbutton">5</button>
        <button @click="props.valorTeclas('6')" class="btn rounded-5 border-none m-2 p-3 colorbutton">6</button>
        <button @click="props.valorTeclas('+')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">+</button>
        <button @click="props.valorTeclas('1')" class="btn rounded-5 border-none m-2 p-3 colorbutton">1</button>
        <button @click="props.valorTeclas('2')" class="btn rounded-5 border-none m-2 p-3 colorbutton">2</button>
        <button @click="props.valorTeclas('3')" class="btn rounded-5 border-none m-2 p-3 colorbutton">3</button>
        <button @click="props.calcular()" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">=</button>
        <button @click="props.valorTeclas('0')" class="btn rounded-5 border-none m-2 p-3 colorbutton --zero">0</button>
        <button @click="props.valorTeclas('.')" class="btn rounded-5 border-none m-2 p-3 colorbutton">.</button>
    </div>
</template>

<style scoped>
.calculator-teclas {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    padding-top: 10px;
}

/*Classe que permite que a tecla zero ocupe mais de uma coluna*/
.--zero {
    grid-column-start: 3;
    grid-column-end: 1;
}

.calculator-teclas>button {
    font-size: 20px;
    font-weight: 600;
    font-family: sans-serif;
}

.calculator-teclas>button:hover {
    border: 1px solid #fff;
    color: #fff;
}

.colorbutton {
    background-color: #131b25;
    box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
    color: #fff;
}

.--green {
    color: greenyellow !important;
}

.--red {
    color: red !important;
}
</style>