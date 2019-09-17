<template>
  <div class='photos-container'>
    <div class='photo-cards'>
    <div v-bind:key="photo.id" v-for="photo in photos">
    <PhotoCard v-bind:photo="photo"/>
    </div>
    </div>
  </div>
</template>

<script>
import PhotoCard from './PhotoCard.vue';

export default {
  name: 'PhotosContainer',
   components: {
    PhotoCard
  },
  props: ['photos', 'homePhoto']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.home-image {
  border: 1px solid black;
  height: 100px;
  width: 400px;
}

.photos-container {
  display: flex;
  flex-direction: column;
}

.photo-cards {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
</style>
