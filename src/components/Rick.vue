
<script>
import * as Vue from 'vue' // in Vue 3
import axios from 'axios'
import VueAxios from 'vue-axios'

let API = 'https://rickandmortyapi.com/api/character';
export default {
  data() {
    return {
      message: 'Hello World!',
      Rick: 'Rickk',
    }
  },
  methods: {
    reverseMessage() {
      this.message = this.message.split('').reverse().join('')
    },
    fetchRick() {
      alert('asd');
      axios.get(API).then((response) => {
        console.log(response.data)
      })
    }
  }
}
</script>

<template>
  <div class="greetings">
    <input v-model="message" placeholder="edit me" />
    <button @click="fetchRick">Fetch</button>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
