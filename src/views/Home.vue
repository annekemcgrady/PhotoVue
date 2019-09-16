<template>
  <div class="home">
    <h1>Welcome to PhotoVue</h1>
    <PhotosContainer v-bind:photos="photos"/>
  </div>
</template>

<script>

// @ is an alias to /src
import PhotosContainer from '@/components/PhotosContainer.vue'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    PhotosContainer
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
  //   created() {
  //   axios.get('')
  //   .then(res => this.photos = res.data)
  //   .catch(error => console.log(error))
  // }
}

</script>
