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
  height: auto;
  width: auto;
  border: 1px solid black;
  margin: 10px;
  padding: 15px;
  box-shadow: -5px 7px 5px 0px rgba(0,0,0,0.5);
}

img {
  height: 200px;
  max-width: 320px;
}
</style>