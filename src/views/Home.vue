<template>
  <div class="home">
    <p v-if=isLoading> Loading ...</p>
    <h1>Welcome to PhotoVue</h1>
    <p>What would you like to see today?<br>Enter a word below and find your inspiration...</p>
     <img v-bind:homePhoto="homePhoto" :src=homePhoto.urls.full alt="Relevant photo">
    <SearchPhoto v-on:search-photo="searchPhoto"/>
    <PhotosContainer v-bind:photos="photos" v-bind:homePhoto="homePhoto" />
  </div>
</template>

<script>
// @ is an alias to /src
import PhotosContainer from '@/components/PhotosContainer.vue'
import SearchPhoto from '@/components/SearchPhoto.vue'
import axios from 'axios'
require('dotenv').config();
import { VUE_APP_ACCESS_KEY } from '@/components/apiKeys.js'
var api_key = process.env.VUE_APP_ACCESS_KEY;

console.log(api_key)

export default {
  name: 'home',
  components: {
    PhotosContainer,
    SearchPhoto
  }, 
  data() {
    return {
      homePhoto: {},
      photos: [],
      isLoading: true,
      error: ''
      }  
    }, 
    methods: {
      searchPhoto(searchWord) {
    
      const { title } = searchWord;

      axios.get(`https://api.unsplash.com/search/photos/?client_id=${VUE_APP_ACCESS_KEY}&query=${title}`)
      .then(res => this.photos = res.data.results)
      .catch(error => this.error = error.message)
    }
  },
  created() {
    axios.get(`https://api.unsplash.com/photos/random?client_id=${VUE_APP_ACCESS_KEY}`)
    .then(object => this.homePhoto = object.data)
    .catch(error => this.error = error.message)

    this.isLoading = false;
  }
}
 
</script>

<style scoped>

p {
  font-size: 1.2em;
}

img {
  height: 300px;
  width: auto;
}
</style>