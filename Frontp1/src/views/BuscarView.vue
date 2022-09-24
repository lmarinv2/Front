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
import axios from 'axios';
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
      const headers = {
          'Access-Control-Allow-Origin': '*',
          'Access-Control-Allow-Headers': '*',
          'Access-Control-Allow-Credentials': true,
          'Content-Type': 'application/json',
        }
      axios.post(
        '/http://52.204.153.196/records/create',
        {key: this.$data.key,},
        { headers })
        .then(response => (this.respuesta = response.data));
    }
  }
})
</script>