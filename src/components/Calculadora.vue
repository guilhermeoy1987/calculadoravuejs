<script setup>
defineProps(['numeroA', 'numeroB', 'operacao', 'resultado']);
defineEmits(['update:numeroA', 'update:numeroB', 'update:operacao']);
</script>

<template>
  <div>

    <!-- PRIMEIRA LINHA (inputs lado a lado) -->
    <div class="row g-3 justify-content-center">
      <div class="col-md-4">
        <input
          type="number"
          :value="numeroA"
          @input="$emit('update:numeroA', $event.target.value)"
          class="form-control"
          placeholder="0"
        >
      </div>

      <div class="col-md-4">
        <input
          type="number"
          :value="numeroB"
          @input="$emit('update:numeroB', $event.target.value)"
          class="form-control"
          placeholder="0"
        >
      </div>
    </div>

    <!-- SEGUNDA LINHA (select sozinho embaixo) -->
    <div class="row mt-3 justify-content-center">
      <div class="col-md-4">
        <select
          :value="operacao"
          @change="$emit('update:operacao', $event.target.value)"
          class="form-select bg-primary text-white text-center"
        >
          <option value="somar">Soma</option>
          <option value="subtrair">Subtração</option>
          <option value="multiplicar">Multiplicação</option>
          <option value="dividir">Divisão</option>
        </select>
      </div>
    </div>

    <!-- Resultado -->
    <div class="row mt-4">
      <div class="col-12">
        <div class="p-3 text-center bg-light border rounded shadow-inner">
          <h3 class="mb-0">
            Resultado: <span class="text-primary">{{ resultado }}</span>
          </h3>
        </div>
      </div>
    </div>

  </div>
</template>