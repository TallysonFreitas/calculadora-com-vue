<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    operacao:'sub',
    numero1:0,
    numero2:0,
    resultado: 0,
  })

  function adi(){
    estado.resultado = parseInt(estado.numero1) + parseInt(estado.numero2)
  }

  function sub(){
    estado.resultado = parseInt(estado.numero1) - parseInt(estado.numero2)
  }

  function mult() { 
    estado.resultado = parseInt(estado.numero1) * parseInt(estado.numero2)
  }

  function div() {  
    estado.resultado = parseInt(estado.numero1) / parseInt(estado.numero2)
  }

  function pot() {  
    estado.resultado = parseInt(estado.numero1) ** parseInt(estado.numero2)
  }

  function numero1() { 
  operacao()
  }

  function numero2() { 
  operacao()
  }

  function operacao() {  
    switch(estado.operacao){
      case 'adi':
      return adi()
      case 'sub':
      return sub()
      case 'mul':
      return mult()
      case 'div':
      return div()
      case 'pot':
      return pot()
    }
  }
</script>

<template>
  <div class="container">
    <div class="row d-flex">
      <form action="" class="form d-flex w-100 justify-content-between p-5">
        <div class="w-100 p-3">
          <label for="" class="form-label mt-5">numero 1</label>
          <input class="form-control" type="number" @keyup="evento=>{estado.numero1 = evento.target.value, numero1()}">
        </div>
        <div class="w-100 p-3">
          <label for="" class="form-label mt-5">numero 2</label>
          <input class="form-control" type="number" @keyup="evento=>{estado.numero2 = evento.target.value, numero2()}">
        </div>
      </form>
      <div class="w-100 justify-content-center d-flex">
        <select @change="evento=>estado.operacao=evento.target.value" >
          <option value="sub">Subtracao</option>
          <option value="adi">Adicao</option>
          <option value="mul">Multiplicacao</option>
          <option value="div">Divisao</option>
          <option value="pot">Potenciacao</option>
        </select>
        {{ estado.numero1 }}
        {{ estado.numero2 }}
        {{  estado.operacao  }}
      </div>
    </div>
    {{ estado.resultado }}
  </div>
</template>

<style scoped>

</style>
