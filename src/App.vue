<template>
  <div id="app">

    <Header></Header>

    <div class="container" id="search-container">
      <div class="row">
        <div class="col-sm-6 ml-auto mr-auto">

          <AutoCompleteSearch @keyup="refreshAutoComplete($event)" ref="autoComplete"></AutoCompleteSearch>

        </div>

      </div>
    </div>

  </div>
</template>

<script>

import Footer from './components/Footer';
import Header from './components/Header';
import AutoCompleteSearch from './components/AutoCompleteSearch';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Footer,
    Header,
    AutoCompleteSearch
  },
  data() {
    return {
    }
 },
 methods: {

    search(limit = 20) {

     // if(!this.searchValue) return;

      let vm = this;

      axios.get('http://en.wikipedia.org/w/api.php', {
        params: {
          format: 'json',
          action: 'query',
          generator: 'search',
          gsrnamespace: 0,
          gsrsearch: 'test',
          gsrlimit: 10,
          prop: 'pageimages|extracts',
          pilimit: 'max',
          piprop: 'original',
          exintro: true,
          explaintext: true,
          exsentences: 1,
          exlimit: 'max',
          origin: '*'
        }
      }).then((res) => {
        console.log(res.request.responseURL);
        console.log(res.data);
      }).catch((error) => {
        console.error(error);
      });

    },

    refreshAutoComplete(value, limit = 10) {

     // if(!this.searchValue) return;

      let vm = this;

      axios.get('http://en.wikipedia.org/w/api.php', {
        params: {
          action: 'opensearch',
          search: value, 
          limit: limit,
          namespace: 0,
          origin: '*',
          format: 'json'
        }
      }).then((res) => {
        console.log(res.data);
        vm.$refs.autoComplete.itensAutoComplete = res.data[1];
      }).catch((error) => {
        console.error(error);
      });

    }
  }
}
</script>


<style lang="scss" scoped>

  $primaryColor: "#000";
  
  #search-container {
    margin-top: -20px;
    
    .search-input {
      border: 1px solid #b2b2b2 !important;
    }

  }

  .input-group-text.dark {
    color: $primaryColor !important;
    background-color: $primaryColor !important;
    border: 1px solid #b2b2b2 !important;
  }

</style>