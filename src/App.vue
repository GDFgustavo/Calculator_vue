<script setup>
import { reactive } from 'vue';

const estado = reactive({
  display: '',
  resultado: 0,
  operadores: ['+', '-', '*', '/', '%'],
  error: '',
  eVisivel: false
})

function valorTeclas(value) {
  if (estado.operadores.includes(value) && estado.operadores.includes(estado.display.slice(-1))) { //Restrigindo que adicione dois operadores juntos
    return;
  }

function limitaCaracteres() {
  if (estado.display.length <= 150) {

  }else {
    back()
  }
}
  estado.display += value
  limitaCaracteres()
}

function limpaDisplay() {
  estado.display = ''
  estado.resultado = 0
}

// Apaga um elemento por vez
function back() {
  estado.display = estado.display.substring(0, estado.display.length -1)
}

// Responsável pelas operações aritméticas
function calcular () {
  try {
    estado.resultado = eval(estado.display)
  }catch {
    estado.error = 'Formato Inválido';
    estado.eVisivel = true
    setTimeout(() => {
      estado.eVisivel = false
      estado.error = ''
        }, 2000);
  }
}

</script>

<template>
  <div class="container">
    <div class="calculator rounded-4">
      <div class="calculator-display text-end">
        <div class="display text-break mb-4">
          <h1 class="text-light" :class="{ 'small-text': estado.display.length >= 12}">{{ estado.display }}|</h1>
        </div>
      </div>
      <div class="calculator-result d-flex justify-content-end text-break mt-4">
        <h2 class="text-secondary fw-normal">{{ estado.resultado }}</h2>
      </div>
      <div class="calculator-back d-flex justify-content-end mt-2 mb-3">
        <button @click="back" class="btn">
          <i class="bi bi-x-circle fs-5 --green"></i>
        </button>
      </div>
      <div class="calculator-msg-error">
        <h3 class="fs-5 text-white text-center">{{ estado.error }}</h3>
      </div>
      <div class="calculator-teclas"> <!--Adicionando as teclas-->
        <button @click="limpaDisplay('C')" class="btn rounded-5 border-none m-2 p-3 colorbutton --red">C</button>
        <button @click="valorTeclas('%')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">%</button>
        <button @click="valorTeclas('/')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">÷</button>
        <button @click="valorTeclas('*')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">x</button>
        <button @click="valorTeclas('7')" class="btn rounded-5 border-none m-2 p-3 colorbutton">7</button>
        <button @click="valorTeclas('8')" class="btn rounded-5 border-none m-2 p-3 colorbutton">8</button>
        <button @click="valorTeclas('9')" class="btn rounded-5 border-none m-2 p-3 colorbutton">9</button>
        <button @click="valorTeclas('-')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">-</button>
        <button @click="valorTeclas('4')" class="btn rounded-5 border-none m-2 p-3 colorbutton">4</button>
        <button @click="valorTeclas('5')" class="btn rounded-5 border-none m-2 p-3 colorbutton">5</button>
        <button @click="valorTeclas('6')" class="btn rounded-5 border-none m-2 p-3 colorbutton">6</button>
        <button @click="valorTeclas('+')" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">+</button>
        <button @click="valorTeclas('1')" class="btn rounded-5 border-none m-2 p-3 colorbutton">1</button>
        <button @click="valorTeclas('2')" class="btn rounded-5 border-none m-2 p-3 colorbutton">2</button>
        <button @click="valorTeclas('3')" class="btn rounded-5 border-none m-2 p-3 colorbutton">3</button>
        <button @click="calcular()" class="btn rounded-5 border-none m-2 p-3 colorbutton --green">=</button>
        <button @click="valorTeclas('0')" class="btn rounded-5 border-none m-2 p-3 colorbutton --zero">0</button>
        <button @click="valorTeclas('.')" class="btn rounded-5 border-none m-2 p-3 colorbutton">.</button>
      </div>
    </div>
  </div>

</template>

<style>
#app {
  background-color: #683030;
}
</style>

<style scoped>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/*Classe para diminuir a fonte os valores exibido no display*/
.small-text {
  font-size: 26px;
  transition: all .3s;
}

.container {
  max-width: 100%;
  width: 400px;
  margin: 0 auto;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.calculator {
  background-color: #131b25;
  box-shadow: rgba(0, 0, 0, 0.19) 0px 10px 20px, rgba(0, 0, 0, 0.23) 0px 6px 6px;
  padding: 8px;
}

.calculator-display {
  height: 68px;
  overflow-y: scroll
}

::-webkit-scrollbar {
    width: 0px;
}

.calculator-result {
  margin-right: 13px;
}

.calculator-back {
  border-bottom: 1px solid #282828;
}

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

.calculator-teclas > button {
  font-size: 20px;
  font-weight: 600;
  font-family: sans-serif;
}

.calculator-teclas > button:hover {
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