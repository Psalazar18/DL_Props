<template>
  <div id="app">
        <Formulario :listOfTasks="Datos" @addingTask="AgregarTareas" @eliminarTarea="deleteTask"/>
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue'

export default {
  name: 'App',
  data() {
    return {
      Datos: []
    }
  },
  components: {
    Formulario
  },
  methods: {
    AgregarTareas(datos){
      console.log(datos);
      this.Datos.push(datos);
    },
    deleteTask(index){
      this.Datos.splice(index,1)
    }
  },
}
</script>

<style>

</style>
