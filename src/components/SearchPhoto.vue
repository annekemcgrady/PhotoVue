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
      e.preventDefault();
      const searchWord = {
        title: this.title
      }
      this.$emit('search-photo', searchWord)
      this.title = '';
    }
  }
  }
</script>


<style scoped>

.search-form {
  height: 100px;
  width: 100%;
  border:  1px solid darkcyan;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  height: 54px;
  width: 200px;
  margin-left: 5px;
  background-color: darkcyan;
}

input {
  height: 50px;
  width: 200px;
  border: 1px solid darkcyan;
}




</style>