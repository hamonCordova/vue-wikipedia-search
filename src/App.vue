<template>
  <div id="app">
    <Header></Header>
    <Footer></Footer>

    <div class="container" id="search-container">
      <div class="row">
        <div class="col-sm-6 ml-auto mr-auto">
            <input v-model="searchValue" class="search-input form-control" placeholder="Type Somenthing...">
        </div>
      </div>
    </div>
  
  </div>
</template>

<script>

import Footer from './components/Footer';
import Header from './components/Header';

export default {
  name: 'app',
  components: {
    Footer,
    Header
  },
  data() {
    return {
      searchValue: ''
    }
 },
  watch: {
    searchValue() {
      alert(this.searchValue);
    }
  }
}
</script>

<style>
  html, body {
    background: rgb(158, 158, 158);
  }
</style>

<style lang="scss" scoped>
  
  #search-container {
    margin-top: 25px;
    
    .search-input {
      width: 100%;
    }

  }

</style>