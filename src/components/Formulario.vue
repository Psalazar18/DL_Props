<template>
  <form @submit.prevent= "Agregar">
    <div class="input-group m-5 container">
      <input type="text" class="form-control" placeholder="Ingrese una tarea" v-model="task">
      <div class="input-group-append">
        <button class="btn btn-outline-secondary bg-warning text-dark" type="submit">Agregar</button>
      </div>
    </div>
    <div class="mx-5">
      <ul >
        <li v-for="(data,index) in listOfTasks" :key="index">{{task}} 
          <button class="bg-danger text-white" @click="eliminar(index)"><font-awesome-icon :icon="['fas', 'times']"/>
          </button> 
        </li>
      </ul>
    </div>
  </form>
</template>

<script>
export default {
  name: 'Formulario',
  data() {
    return {
      task: '',
    }
  },
  props: {
    listOfTasks: {
      type: Array,
      required: true
    }
  },
  methods: {
    Agregar(){
      let dataTask = this.task;
      this.$emit('AgregarTareas', dataTask)    
    },
    eliminar(index){
      this.$emit('eliminarTarea', index)
    }
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
