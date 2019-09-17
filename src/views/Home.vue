<template>
  <div class="home">
    <p class='loading' v-if="isLoading"> Loading ...</p>
    <p class='error' v-if="error"> Loading ...</p>
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

      axios.get(`https://api.unsplash.com/search/photos/?client_id=${process.env.VUE_APP_ACCESS_KEY}&query=${title}`)
      .then(res => this.photos = res.data.results)
      .catch(error => this.error = error.message)
    }
  },
 
  created() {
    axios.get(`https://api.unsplash.com/photos/random?client_id=${process.env.VUE_APP_ACCESS_KEY}`)
    .then(object => this.homePhoto = object.data)
    .catch(error => this.error = error.message)

    this.isLoading = false;
  }
}
 
</script>

<style scoped>

h1 {
  font-size: 2.5em;
  margin: 10px;
}

p {
  font-size: 1.2em;
}

.error, .loading {
  color: darkcyan;
  font-size: 2em;
}

img {
  height: 200px;
  width: auto;
}
</style>