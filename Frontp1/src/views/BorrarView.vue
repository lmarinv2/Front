<template>
  <div class="Borrar">
    <h1>Borrar</h1>
    <router-link to="/" tag="button"
      >volver</router-link
    >
    <p>Value: {{ value }}</p>
    <input type="text" v-model="value" placeholder="" />
    <p></p>
    <button v-on:click="answer">Guardar</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      value: "value",
    }
  },
  methods: {
    answer() {
      fetch("http://52.204.153.196/delete/"+this.value, {
        method: "DELETE", // *GET, POST, PUT, DELETE, etc.
        mode: "cors",
        cache: "no-cache",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(this.$data), // body data type must match "Content-Type" header
      }).then((data) =>data.json()).then((data)=>{console.log(data)});
    }
  }
})
</script>