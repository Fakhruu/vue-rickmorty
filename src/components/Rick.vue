
<script>
import * as Vue from 'vue' // in Vue 3
import axios from 'axios'
import VueAxios from 'vue-axios'

let API = 'https://rickandmortyapi.com/api/character/2,435,13,44,112';
export default {
  data() {
    return {
      rickAPI: false,
    }
  },
  methods: {
    fetchRick() {
      axios.get(API).then((response) => {
        this.rickAPI = response.data;
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
  <div v-if="rickAPI">
    <div v-for="rick in rickAPI" :key="rick.name">
      <div class="max-w-sm rounded overflow-hidden shadow-lg">
  <img class="w-full" v-bind:src="rick.image" alt="Sunset in the mountains">
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">{{rick.name}}</div>
    <p class="text-gray-700 text-base">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, nulla! Maiores et perferendis eaque, exercitationem praesentium nihil.
    </p>
  </div>
  <div class="px-6 pt-4 pb-2">
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#photography</span>
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#travel</span>
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#winter</span>
  </div>
</div>
  </div>
  </div>

</template>
