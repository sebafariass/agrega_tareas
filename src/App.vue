<template>
  <div class="contenido"> <!-- div unico -->
    <h1 class="titulo">Lista de Tareas</h1> <!--titulo -->

    <!-- input con v-model para realizar two way data binding-->
    <input  v-model="tarea" type="text" placeholder="Escribe tu Tarea" />
    <!-- boton para generar interacción, asi mismo llamo a la función 
     mediante el evento click para ir agregando el contenido y con la funcion
    agregar de por medio-->
    <button @click="agregar_tarea" class="boton_add">Agregar Tarea</button>
 

   <h4>Listado de Tareas Ingresadas</h4> <!--subtitulo-->

    <!--  recorremos el arreglo con la directiva v-for, asi mismo
    usamos directiva v-bind  para vincular atributos html en el modelo,
    mencionamos el llamado al evento @eliminar para borrar contenido tarea
    y usamos :key para mantener el orden en caso de posibles errores -->

    <tarea   
      v-for="(tarea, i) in tareas"
      :tarea="tarea"
      :indice="i"
      :key="i"
      @eliminar_tareita="eliminar_tarea"
    ></tarea>
     <!--llamamos evento @eliminar con funcion eliminar_tarea --> 
  </div>
</template>

<script>

import tarea from "./components/Tarea"; //componente hijo tarea - import
export default {
  
  nombre: "listaTareas", // nombre de componente
 
  data() {
    /* con funcion data podremos retornar un string vacio 
    en los cuales serán guardados los datos del input
    junto a ello un array vacio donde se guardan los datos de estos mismos */
    return {
      tarea: "",
      tareas: [],
    };
  },
 
  components: { //componente hijo "tarea"
    tarea,
  },
  // Métodos
  methods: {

    agregar_tarea() { //funcion agregar_tarea con metodo push para ir ingresando datos al array vacio desde nuestro string 
      this.tareas.push(this.tarea); 
      this.tarea = "";
    },
   
    eliminar_tarea(indice) {  // con el método splice elimino un objeto(tarea) del array tareas
      this.tareas.splice(indice, 1);
    },
  },
};
</script>

<style></style>
