<template>
    <div>   
        <div class="input-group">
            <div class="input-group-prepend">
                <span class="input-group-text bg-dark"><span class="oi text-white" data-glyph="magnifying-glass"></span></span>
            </div>
            <input type="text" @keyup="debounceKeyup()" @keyup.enter="$emit('keyup.enter')" v-model.trim="searchValue" class="search-input form-control" placeholder="Type Somenthing...">

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
            searchValue: '',
            itensAutoComplete: [],
            debounceKeyup: null,
        }
    },
    created() {
        this.debounceKeyup = _.debounce(this.keyupEvent, 200);
    },
    methods: {
        keyupEvent() {
            this.$emit('keyup', this.searchValue);
        },
    }
  
}
</script>