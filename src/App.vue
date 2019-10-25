<template>
  <div id="app">

    <Header></Header>

    <div class="container">
      
      <div class="row" id="search-container">
        <div class="col-sm-12 col-md-6 ml-auto mr-auto">
          <AutoCompleteSearch @search="searchArticles($event)" @keyup="onKeyUpAutoComplete($event)" ref="autoComplete"></AutoCompleteSearch>
          <p>{{ message }} </p>
        </div>
      </div>

      <div class="row articles" v-for="(article, index) in articleList" v-bind:key="index">
        <div class="col-sm-12">
          <ArticleItem :article="article"></ArticleItem>
        </div>
      </div>

    </div>

  </div>
</template>

<script>

import axios from 'axios';
import Footer from './components/Footer';
import Header from './components/Header';
import AutoCompleteSearch from './components/AutoCompleteSearch';
import ArticleItem from './components/ArticleItem';

export default {
  name: 'app',
  components: {
    Footer,
    Header,
    AutoCompleteSearch,
    ArticleItem
  },
  data() {
    return {
      articleList: [],
      message: '',
    }
 },
 created() {
   setTimeout(() => {
    this.searchArticles('google');
   }, 10);
 },
 methods: {

    searchArticles(value, limit = 20) {

      let vm = this;

      vm.$refs.autoComplete.isLoading = true;
      vm.articleList = [];
      vm.message = '';

      axios.get('http://en.wikipedia.org/w/api.php', {
        params: {
          format: 'json',
          action: 'query',
          generator: 'search',
          gsrnamespace: 0,
          gsrsearch: value,
          gsrlimit: limit,
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
        
        if(res.data.query && res.data.query.pages) {
          vm.articleList = res.data.query.pages;
          vm.message = '';
        } else {
          vm.message = 'No Articles Found';
        }

        vm.$refs.autoComplete.clearAutoComplete();
        vm.$refs.autoComplete.isLoading = false;

      }).catch((error) => {
        console.error(error);
      });

    },

    refreshAutoComplete(value, limit = 6) {

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
        if(res) {
          vm.$refs.autoComplete.clearAutoComplete();
          vm.$refs.autoComplete.itensAutoComplete = res.data[1].slice(1);
        }
      }).catch((error) => {
        console.error(error);
      });

    },

    onKeyUpAutoComplete(event) {

      let value = event.target.value;

      if(event.key == 'Enter') {

         if(value) {
          this.$refs.autoComplete.clearAutoComplete();
          this.searchArticles(value);
        } else {
          this.articleList = [];
        }

      } else {
        this.refreshAutoComplete(value);
      }

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

  .container {
    padding-bottom: 40px;
  }

</style>