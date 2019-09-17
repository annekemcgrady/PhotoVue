<template>
   <div class="photo-card" >
      <p>{{photo.description}}</p>
      <img :src="photo.url" alt="Relavant photo">
    </div>
</template>

<script>
export default {
  name: 'PhotoCard',
  props: ['photo']
}
</script>

<style scoped>
.photo-card {
  height: 300px;
  width: 350px;
  border: 1px solid black;
  margin: 10px;
}

img {
  height: 200px;
  width: auto;
}
</style>