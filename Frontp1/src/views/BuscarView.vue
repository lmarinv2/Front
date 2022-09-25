<template>
  <div class="Buscar">
    <h1>Buscar</h1>
    <router-link to="/" tag="button"
      >volver</router-link
    >
    <p>Key: {{ key }}</p>
    <input type="text" v-model="key" placeholder="" />
    <p></p>
    <button v-on:click="answer">Buscar</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      key: "key",
      respuesta: null
    }
  },
  methods: {
    answer() {
      fetch("http://52.204.153.196/get/"+ this.$data.key, {
        method: "GET", // *GET, POST, PUT, DELETE, etc.
        mode: "cors",
        cache: "no-cache",
        headers: {
          "Content-Type": "application/json",
        },
        //body: JSON.stringify(this.$data), // body data type must match "Content-Type" header
      }).then((data) =>data.json()).then((data)=>{console.log(data)});
    }
  }
})
</script>