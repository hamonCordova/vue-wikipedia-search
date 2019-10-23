<template>
  <div id="app">
    <Header></Header>

    <div class="container" id="search-container">
      <div class="row">
        <div class="col-sm-6 ml-auto mr-auto">
            <input v-model="searchValue" class="search-input form-control" placeholder="Type Somenthing...">
        </div>
      </div>
    </div>

    <Footer></Footer>
  
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
    }
  }
}
</script>

<style>
  html, body {
    background: #f1f1f1
  }
</style>

<style lang="scss" scoped>
  
  #search-container {
    margin-top: -20px;
    
    .search-input {
      width: 100%;
      border: 1px solid #b2b2b2 !important;
    }

  }

</style>