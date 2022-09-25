<template>
  <div class="Listar">
    <h1>listar</h1>
    <router-link to="/" tag="button"
      >volver</router-link
    >
    <button v-on:click="answer">listar</button>
    
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      value: "value",
      key: "key",
      respuesta: null
    }
  },
  methods: {
    answer() {
      fetch("http://52.204.153.196/getall", {
        method: "GET", // *GET, POST, PUT, DELETE, etc.
        mode: "cors",
        cache: "no-cache",
        headers: {
          "Content-Type": "application/json",
        },
       // body: JSON.stringify(this.$data), // body data type must match "Content-Type" header
      }).then((data) =>data.json()).then((data)=>{console.log(data)});
    }
  }
})
</script>