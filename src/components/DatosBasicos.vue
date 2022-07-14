<template>
  <h2>Datos Básicos {{tipo}}</h2>

  <div>
      <h4>Nombre {{tipo}}</h4>
      <input type="text">
      <h4>Apellido {{tipo}}</h4>
      <input type="text">
      <h4>Correo {{tipo}}</h4>
      <input type="text">
  </div>
      
</template>

<script>
export default {
    name: "DatosBasicos",
    props:{
        nombre: String,
        apellido: String,
        correo: String,
        tipo: String,
    },
     data(){
        return{
            nombre: this.nombre,
            apellido: this.apellido,
            correo: this.correo,
            tipo: this.tipo
        }
    }
}
</script>

<style>

</style>