<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!--"v-bind" permite evaluar como un expresion JavaScript-->
  <Contador titulo="Titulo 1" v-bind:inicio="valorInicio"/>
  <Contador2 titulo="Titulo 3" v-bind:inicio="-1"/>
  <DatosBasicos v-bind:tipo="tipoE"/>
  <DatosBasicos v-bind:tipo="tipoP"/>
  <Calculadora/>
</template>

<script>
import Contador from './components/Contador.vue'
import Contador2 from './components/Contador2.vue'
import Calculadora from './components/Calculadora.vue'
import DatosBasicos from './components/DatosBasicos.vue'

//Option API
export default {
  name: 'App',
  data(){
    return{
      valorInicio: 35,
      tipoE: 'Estudiante',
      tipoP: 'Profesor'
    };
  },
  components: {
    Contador,
    Contador2,
    DatosBasicos,
    Calculadora
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
