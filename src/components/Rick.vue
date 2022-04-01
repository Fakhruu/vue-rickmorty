
<script>
import * as Vue from 'vue' // in Vue 3
import axios from 'axios'
import VueAxios from 'vue-axios'

let API = 'https://rickandmortyapi.com/api/character';
export default {
  data() {
    return {
      rickAPI: false,
      rickName:'',
    }
  },
  methods: {
    fetchRick() {
      let newAPI = API + "?&name="+this.rickName;
      axios.get(newAPI).then((response) => {
        this.rickAPI = response.data.results;
        console.log(response.data)
      })
    }
  }
}
</script>

<template>
  <div class="greetings">
          <input v-model="rickName" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="Search">
    <button @click="fetchRick" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Fetch</button>
  </div>
  <div v-if="rickAPI" class="grid grid grid-cols-4 gap-4">
    <div v-for="rick in rickAPI" :key="rick.ID" class="">
      <div class="max-w-sm rounded overflow-hidden shadow-lg">
  <img class="w-full" v-bind:src="rick.image" alt="Sunset in the mountains">
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">{{rick.name}}</div>
    <p class="text-gray-700 text-base">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, nulla! Maiores et perferendis eaque, exercitationem praesentium nihil.
    </p>
  </div>
  <div class="px-6 pt-4 pb-2">
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">{{rick.gender}}</span>
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">{{rick.species}}</span>
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">{{rick.location.name}}</span>
  </div>
</div>
  </div>
  </div>

</template>
