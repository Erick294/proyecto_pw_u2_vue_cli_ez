<template>
  <img src="https://via.placeholder.com/250" alt="No encontrado" >
  <div class="bg-oscuro"></div>

  <div class="pregunta-container">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
    <p>Recuerda terminar con un signo de interrogación (?)</p>

    <h2>{{pregunta}}</h2>
    <h1>SI, NO, ... Pensando</h1>
  </div>
</template>

<script>
export default {
  data(){
    return{
      pregunta: "Hola mundo"
    }
  },
  methods:{
    async obtenerRespuesta(){
      const data = await fetch('https://yesno.wtf/#api').then((resp)=>resp.jason);
      console.log('Respuesta: ' + data);
    }
  },
  watch:{
    pregunta(value, oldValue){
      console.log('Actual: ' + value)
      console.log('Anterior: ' + oldValue)

      if(value.includes('?')) return;
      console.log('Sin incluye');
      //Llamar y consultar al API
    }
  }
}
</script>

<style scoped>
.bg-oscuro{
    background-color:(0,0,0,4);
}

img, .bg-oscuro{
    height: 100vh;
    left: 0px;
    max-height: 100%;
    max-width: 100%;
    position: fixed;
    top: 0px;
    width: 100vw;
}

.pregunta-container{
  position: relative;
  z-index: 99;
}

input{
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}

input:focus{
  outline: none;
}

p{
  color: azure;
  font-size: 20px;
  margin-top: 0px;
}

h1,h2{
  color: azure;
}

h2{
  margin-top: 150px;
}
</style>
