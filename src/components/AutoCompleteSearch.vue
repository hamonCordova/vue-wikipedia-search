<template>
    <div>   
        <div class="input-group">
            <div class="input-group-prepend">
                <i class=""></i>
                <span class="input-group-text bg-dark">
                    <i :class="[isLoading ? 'fas fa-spinner fa-spin' : 'fas fa-search', 'text-white']"></i>
                </span>
            </div>
            <input type="text" @keyup="debounceKeyup($event)" v-model.trim="searchValue" class="search-input form-control" placeholder="Type Somenthing...">

        </div>

        <ul>
            <li v-for="(item, index) in itensAutoComplete" :key="index">
                {{ item }}
            </li>
        </ul>

    </div>

</template>


<script>

import _ from 'lodash'

export default {
    name: 'AutoCompleteSearch',
    components: {
    },
    data() {
        return {
            isLoading: false,
            searchValue: '',
            itensAutoComplete: [],
            debounceKeyup: null,
        }
    },
    created() {
        this.debounceKeyup = _.debounce(this.keyupEvent, 200);
    },
    methods: {
        keyupEvent(event) {
            if(this.searchValue) {   
                this.$emit('keyup', event);
            } else {
                this.itensAutoComplete = [];
            }
        },
    }
  
}
</script>