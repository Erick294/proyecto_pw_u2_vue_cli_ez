<template>
  <!--Shortcut de v-bind es :-->
  <img v-if="imagen" :src=imagen alt="No encontrado" >
  <div class="bg-oscuro"></div>

  <div class="pregunta-container">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
    <p>Recuerda terminar con un signo de interrogación (?)</p>

  <div v-if="preguntaValida">
    <h2>{{pregunta}}</h2>
    <h1>{{respuesta}}</h1>
  </div>
    
  </div>
</template>

<script>
export default {
  data(){
    return{
      pregunta: "Hola mundo",
      respuesta: null,
      imagen: null,
      preguntaValida: false
    }
  },
  methods:{
    async obtenerRespuesta(){
      //desestructurar el API
      this.respuesta="Pensando..."
      const {answer, image} = await fetch('https://yesno.wtf/api').then(r => r.json());
      console.log('Respuesta:');
      console.log(answer);
      console.log(image);
      this.respuesta = answer;
      this.imagen = image;
    },
    async consultaCovid(){
      const data = await fetch('https://api.covidtracking.com/v1/us/current.json').then(r => r.json());
      const {negative} = data[0];
      console.log(negative);
    }
  },
  //permite observar propiedades reactivas
  watch:{
    pregunta(value, oldValue){
      console.log('Actual: ' + value);
      console.log('Anterior: ' + oldValue);

      if(!value.includes('?')) return;
      this.preguntaValida = true;
      console.log('Si incluye');
      //Llamar y consultar al API
      this.obtenerRespuesta();
      this.consultaCovid();
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
