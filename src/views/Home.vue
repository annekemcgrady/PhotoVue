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

export default {
  name: 'home',
  components: {
    PhotosContainer,
    SearchPhoto
  }, 
  data() {
    return {
      photos: [
        {id: 1, title: "Photo One", url: "fakeurl"},
        {id: 2, title: "Photo Two", url: "fakeurl2"},
        {id: 3, title: "Photo Three", url: "fakeurl3"}
        ]
      }
    }, 
    methods: {
      searchPhoto(searchWord) {
      console.log('searchPhoto on Home firing')
      const { title } = searchWord;
      axios.get('', {
        title,
      })
      .then(res => this.photos = [...this.photos, res.data])
      .catch(error => console.log(error))
    }
    },

  //   created() {
  //   axios.get('')
  //   .then(res => this.photos = res.data)
  //   .catch(error => console.log(error))
  // }
}

</script>
