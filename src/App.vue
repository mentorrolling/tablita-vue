<script setup>
import { ref } from "vue";

const textInput = ref("");
const resultados = ref([]);
const valor=ref('')

const calcularTabla = () => {
valor.value = Number(textInput.value);
  if (!isNaN(valor.value) && valor.value !== 0) {
    resultados.value=[]
    for (let index = 1; index < 11; index++) {
      resultados.value = [
        ...resultados.value,
        `${valor.value} x ${index} = ${valor.value * index}`,
      ];
    }
    console.log(resultados.value);
    textInput.value=''
  } else {
    alert("Ingrese un número");
    textInput.value = "";
    
  }
};

const limpiarCampo=()=>{
  textInput.value=''
}
</script>

<template>
  <main class="main">
    <section>
      <div class="titulo">
        <img src="./assets/calc.png" alt="calc">
        <h3> Tabla de multiplicar</h3>

      </div>
      <form class="section-input" @submit.prevent="calcularTabla">
        <input class="" v-model="textInput" @click="limpiarCampo" type="number" />
        <button type="submit">Probar!</button>
      </form>
    </section>
    <section v-if="resultados.length>0 && valor >0">
      <h3>Tabla del <span>⭐{{ valor }}⭐</span></h3>
      <ul>
        <li v-for="resultado in resultados">
        <span class="lista">{{ resultado }}</span>
        </li>
      </ul>
    </section>
  </main>
</template>

<style scoped>


.titulo{
  display: flex;
  justify-content: center;
  align-items: center;
}
.main{
  background-color: #42D392;
  padding: 10px;
  border-radius: 10px;
  color: #213547;
  
}
.section-input {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
}
.section-input input {
  font-size: 1.5rem;
  border-radius: 10px;
  text-align: center;
}
h3{
  font-size: 2rem;
  margin-top:10px;
  margin-bottom:5px;
}

ul{
  list-style: none;
  padding: 0;
  font-size: 1.5rem;
}
.lista{
  font-size: 1.5rem;
  font-family: Helvetica,Arial, sans-serif;
  font-weight: bold;
}
.numbre-title{
  font-weight: bold;
}
</style>
