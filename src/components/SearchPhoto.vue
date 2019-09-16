<template>
  <div class='search-form'>
    <form @submit="searchPhoto">
      <input v-model="title" type="text" name="title" placeholder="Enter a Search Word...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>


<script>
export default {
  name: "SearchPhoto",
  data() {
    return {
      title: ''
    }
  }, 
  methods: {
    searchPhoto(e)  {
        console.log('SearchPhoto on Form Firing')
      e.preventDefault();
      const searchWord = {
        title: this.title
      }
      //send up to the parent
      this.$emit('search-photo', searchWord)
      this.title = '';
    }
  }
  }
</script>


<style scoped>

.search-form {
  height: 150px;
  width: 100%;
}

input {
  height: 40px;
  width: 150px;
}


</style>