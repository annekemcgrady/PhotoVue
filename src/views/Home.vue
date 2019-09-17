<template>
  <div class="home">
    <h1>Welcome to PhotoVue</h1>
    <SearchPhoto v-on:search-photo="searchPhoto"/>
    <PhotosContainer v-bind:photos="photos"/>
  </div>
</template>

<script>
// @ is an alias to /src
import PhotosContainer from '@/components/PhotosContainer.vue'
import SearchPhoto from '@/components/SearchPhoto.vue'
import axios from 'axios'
import Unsplash from 'unsplash-js';
// import VUE_APP_ACCESS_KEY from '@/apiKeys'
// import VUE_APP_SECRET from '@/apiKeys'

const VUE_APP_ACCESS_KEY='d3e6ac3d3e412a21e2aa1cd7fb00d5f9f4c036887939a8f789162f39aea92236'
const VUE_APP_SECRET='c45b4eaf54223d2a0cf9d5a946a40bff9634405f6da7e53ed2f67b5a3f93915d'

export default {
  name: 'home',
  components: {
    PhotosContainer,
    SearchPhoto
  }, 
  data() {
    return {
      photos: [{id:2, description: 'Fake Photo Description', url: "https://images.unsplash.com/photo-1562184760-a11b3cf7c169?ixlib=rb-1.2.1&q=80&fm=jpg&crop=entropy&cs=tinysrgb&w=400&fit=max&ixid=eyJhcHBfaWQiOjkxNjYzfQ"}]
      }
    }, 
    methods: {
      searchPhoto(searchWord) {
      console.log('searchPhoto on Home firing')
      const { title } = searchWord;

      axios.get(`https://api.unsplash.com/search/photos/?client_id=${VUE_APP_ACCESS_KEY}}&query=${title}`)
      .then(res => this.photos = res.results)
      .catch(error => console.log(error))
    }
  },
  created() {
    axios.get(`https://api.unsplash.com/search/photos/?client_id=${VUE_APP_ACCESS_KEY}}&query=puppy`)
    .then(res => this.photos = res.results)
    .catch(error => console.log(error))
  }
}
 
</script>

<style scoped>

</style>