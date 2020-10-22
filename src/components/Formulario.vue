<template>
  <form @submit.prevent= "Agregar">
    <h1 class="text-center display-4 my-3">¡Mi lista de cosas por hacer!</h1>
    <div class="input-group m-5 container">
      <input type="text" class="form-control" placeholder="Ingrese una tarea" v-model="task">
      <div class="input-group-append">
        <button class="btn btn-outline-secondary bg-warning text-dark" type="submit">Agregar</button>
      </div>
    </div>
    <div class="mx-5">
      <ul>
        <li v-for="(data,index) in listOfTasks" :key="index">{{data}} 
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
      if(this.task != ""){
        let dataTask = this.task;
        this.$emit('addingTask', dataTask);
        this.task= "";         
      }
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
