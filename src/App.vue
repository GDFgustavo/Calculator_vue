<script setup>
  import { reactive } from 'vue';
  import ItensDisplay from './components/ItensDisplay.vue';
  import Teclas from './components/Teclas.vue';


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
      
      <ItensDisplay :display="estado.display" :resultado="estado.resultado" :error="estado.error" :back="back"></ItensDisplay>
      <Teclas :limpa-display="limpaDisplay" :valor-teclas="valorTeclas" :calcular="calcular"></Teclas>
      
    </div>
  </div>

</template>

<!-- Style global -->
<style>
#app {
  background-color: #683030;
}
</style>

<!-- Style dos componentes -->
<style scoped>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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

</style>