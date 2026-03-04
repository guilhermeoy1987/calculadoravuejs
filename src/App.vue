<script setup>
import { ref, computed } from 'vue'
import Calculadora from './components/Calculadora.vue'
import HeaderComponente from './components/HeaderComponente.vue'
import Footer from './components/Footer.vue'

const numeroA = ref(0)
const numeroB = ref(0)
const operacao = ref('somar')

const resultado = computed(() => {
  const a = Number(numeroA.value)
  const b = Number(numeroB.value)
  let valor = 0

  switch (operacao.value) {
    case 'somar':
      valor = a + b
      break
    case 'subtrair':
      valor = a - b
      break
    case 'multiplicar':
      valor = a * b
      break
    case 'dividir':
      valor = b !== 0 ? a / b : 0
      break
  }

  return Number.isInteger(valor) ? valor : valor.toFixed(2)
})
</script>

<template>
  <div class="app-wrapper">
    <div class="container">
      <div class="calculadora-box">

        <HeaderComponente />

        <Calculadora
          v-model:numeroA="numeroA"
          v-model:numeroB="numeroB"
          v-model:operacao="operacao"
          :resultado="resultado"
        />

        <Footer />

      </div>
    </div>
  </div>
</template>

<style>
.app-wrapper {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f3f3f3;
}

.container {
  max-width: 900px;
  width: 100%;
}

.calculadora-box {
  background: linear-gradient(135deg, #763fbf, #5024ee, #173cdf, #aa771c);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
  border: 2px solid #321a99;
  color: white; /* deixa textos visíveis */
}
</style>