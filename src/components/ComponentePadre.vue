<template>
  <h1>Crear una nueva tarea</h1>
  <div class="formulario">
    <label for="input">Tarea: </label>
    <input id="input" type="text" placeholder="Ingresa una nueva tarea" v-model="nuevaLista">

    <button type="button" @click="AgregarTarea">Añadir</button>
    
    <ComponenteHijo :message="message" :agregar="agregar" @borrarTarea="EliminarTarea" /> 
  </div>

</template>

<script>
import ComponenteHijo from '@/components/ComponenteHijo.vue';

export default {
  name: 'ComponentePadre',
  components: {
    ComponenteHijo
  },
  data: () => ({
    agregar: [],
    nuevaLista: "",
    message: "Lista",
  }),
  methods: {
    AgregarTarea() {
      this.agregar.push(this.nuevaLista);
      this.nuevaLista = ""; 
    },
    EliminarTarea(index) {
      this.agregar.splice(index, 1);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #315f8d;
  margin-top: 80px;
}
h1 {
  font-size: 2.3em;
  margin-bottom: 1em;
}
input {
  border: 1.7px solid #4b4b4b;
  padding: 5px;
}
button {
  background-color: #d6e2f5;
  border: 1.7px solid #4b4b4b;
  margin-left: 1px;
  cursor: pointer;
  padding: 5px;
}
</style>