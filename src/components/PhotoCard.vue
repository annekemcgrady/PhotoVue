<template>
   <div class="photo-card" >
      <h3>This is the PhotoCard</h3>
      <p>{{photo.title}}</p>
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
  height: 200px;
  width: 200px;
  border: 1px solid black;
  margin: 10px;
}
</style>