<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    resultado: 0,
    mostraOperador: '',
    numX: 0,
    numY: 0,
  })
</script>

<template>
  <div class="container">
    <header class="mt-4 mb-4 text-center bg-success rounded-2 p-4">
      <h1>Calculadora Aritmetica</h1>
    </header>

    <div class="row">
      <div class="col-8">
        <p class="text-end p-1">Operação:</p>
      </div>
      <div class="col-4">
        <select @change="evento => estado.mostraOperador = evento.target.value" class="form-control" id="select">
          <option id="selecionar" value="">Selecionar</option>
          <option id="soma" value="+">Somar</option>
          <option id="subtracao" value="-">Subtrair</option>
          <option id="multiplicacao" value="*">Multiplicar</option>
          <option id="divisão" value="/">Dividir</option>
        </select>
      </div>
    </div>

    <div class="row mt-4 mb-4">
      <div class="col-3">
        <input @keyup="evento => estado.numX = evento.target.value" type="number" placeholder="Número X" class="form-control">
      </div>
      <div class="col-2">
        <div class="container">
          <h4 class="text-center">{{ estado.mostraOperador }}</h4>
        </div>
      </div>
      <div class="col-3">
        <input @keyup="evento => estado.numY = evento.target.value" type="number" placeholder="Número Y" class="form-control">
      </div>

      <div class="col-4">
        <p class="mt-1 mb-1 fw-bold fs-5">= 
          <span v-if="estado.mostraOperador == '+'">{{ parseFloat(estado.numX) + parseFloat(estado.numY) }}</span>
          <span v-else-if="estado.mostraOperador == '-'">{{ estado.numX - estado.numY }}</span>
          <span v-else-if="estado.mostraOperador == '*'">{{ estado.numX * estado.numY }}</span>
          <span v-else-if="estado.mostraOperador == '/'">{{ estado.numX / estado.numY }}</span>
          <span v-else>Selecione um Operador</span>
        </p>
      </div>
    </div>
    
  </div>
</template>

<style scoped>
  header h1 {
    color: #fff;
  }
</style>
