<template>
  <h2>{{muestraTitulo}}</h2>
  <p>{{numero}} <sup>2</sup> = {{obtenerCuadradoComputado}}</p>
  <p>{{numero}} <sup>2</sup> = {{obtenerCuadradoComputado}}</p>
  <p>{{numero}} <sup>2</sup> = {{obtenerCuadradoComputado}}</p>
  <p>{{numero}} <sup>2</sup> = {{obtenerCuadradoComputado}}</p>
  <p>{{numero}} <sup>2</sup> = {{obtenerCuadradoComputado}}</p>

  <div>
      <button v-on:click="incrementar">Sumar 1</button>
      <button v-on:click="decrementar">Restar 1</button>
  </div>
</template>

<script>
export default {
    name: "Contador2",
    props:{
        titulo: String,
        inicio: {
            type: Number,
            required: false, 
            default: 25,
            validator(value){
                //validacion que retorne un true o false
                return value > 0
            }
        }
    },
    data(){
        return{
            numero: this.inicio
        }
    },
    methods:{
        obtenerCuadrado(){
            console.log("Esta dentro del calculo cuadrado")
            return this.numero * this.numero
        },
        incrementar(){
            //return this.numero++
            return this.numero++
        },
        decrementar(){
            return this.numero--
        }
    }, 
    //Computado se declara como un metodo normal, se ejecuta una vez si se encuentra duplicado
    //Computado no puede tener parámetros
    computed:{
        obtenerCuadradoComputado(){
            console.log("Aqui entro cuadrado computado")
            return this.numero * this.numero
        }, 
        muestraTitulo(){
              return this.titulo || "Titulo vacío";
        }
    }
}
</script>

<style>
button{
    background-color: #64BB87;
    border-radius: 5px;
    color: white;
    margin: 0px 5px;
    cursor: pointer;
}

button:hover{
    background-color:darkslategray;
    transition: 0.9s ease-in-out;
}
</style>