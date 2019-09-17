<template>
   <div class="photo-card" >
      <img :src=photo.urls.small alt="Relevant photo">
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
  width: 330px;
  border: 1px solid black;
  margin: 10px;
  padding: 5px;
}

img {
  height: 200px;
  max-width: 320px;
}
</style>