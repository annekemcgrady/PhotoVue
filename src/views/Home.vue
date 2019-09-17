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
import { VUE_APP_ACCESS_KEY} from '@/components/apiKeys.js'

export default {
  name: 'home',
  components: {
    PhotosContainer,
    SearchPhoto
  }, 
  data() {
    return {
      homePhoto: {},
      photos: [{id:2, description: 'Fake Photo Description', url: "https://images.unsplash.com/photo-1562184760-a11b3cf7c169?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=400&fit=max&ixid=eyJhcHBfaWQiOjkxNjYzfQ"}],
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

img {
  height: 300px;
  width: auto;
}
</style>