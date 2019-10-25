<template>
    <div>   
        <div class="input-group">
            
            <div class="input-group-prepend">
                <i class=""></i>
                <span class="input-group-text bg-danger">
                    <i :class="[isLoading ? 'fas fa-spinner fa-spin' : 'fas fa-search', 'text-white']"></i>
                </span>
            </div>

            <input type="text"  @keyup="debounceKeyup($event)" 
                @keyup.down="moveSelectedItem(-1)" @keyup.up="moveSelectedItem(1)"  @blur="debounceBlur()" 
                v-model.trim="searchValue" class="search-input form-control" placeholder="Type Somenthing...">
            
            <ul class="autocomplete">
                <li @click="selectByIndex(index)" @mouseover="itemSelected = index"
                 :class="[itemSelected == index ? 'active' : '', 'autocomplete-item']" v-for="(item, index) in itensAutoComplete" :key="index">
                  
                    <span>{{ item }}</span>

                </li>
            </ul>

        </div>

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
            lastSearchValue: '',
            itensAutoComplete: [],
            itemSelected: -1,
            debounceKeyup: null,
            debounceBlur: null
        }
    },
    created() {
        this.debounceKeyup = _.debounce(this.keyupEvent, 300);
        this.debounceBlur = _.debounce(this.clearAutoComplete, 100);
    },
    methods: {
        keyupEvent(event) {

            let keyPressed = event.key;
            let keysAuthorized = ['ArrowDown', 'ArrowUp', 'ArrowRight', 'ArrowLeft']
            
            if(keysAuthorized.includes(keyPressed)) return;
        
            if(!this.searchValue) {
                this.itensAutoComplete = [];
            }
             
            this.lastSearchValue = this.searchValue;
            this.$emit('keyup', event);

        },
        clearAutoComplete() {
            this.itensAutoComplete = [];
            this.itemSelected = -1;
        },
        search() {
            this.$emit('search', this.searchValue);
        },
        selectByIndex(index) {
            let value = this.itensAutoComplete[index];
            this.searchValue = value;
            this.lastSearchValue = value;
            this.search();
        },
        moveSelectedItem(count) {

            let maxLength = this.itensAutoComplete.length;
            let newIndex = this.itemSelected - count;

            if(newIndex > maxLength) {
                newIndex = 0
            } else if(newIndex < -1) {
                newIndex = maxLength - 1;
            }

            this.itemSelected = newIndex; 

            if(this.itemSelected == maxLength || this.itemSelected == -1) {
                this.searchValue = this.lastSearchValue;
            } else {
                this.searchValue = this.itensAutoComplete[newIndex];
            }
        
        }
    }
  
}
</script>

<style lang="scss" scoped>

    input[type="text"], textarea {
        outline: none;
        box-shadow:none !important;
        border:1px solid #ccc !important;
    }

    .autocomplete {
        position: absolute;
        top: 37px;
        z-index: 1;
        background: #fff;
        width: 100%;
        border: 1px solid #ccc;
        border-radius: 0 0 10px 10px;
        padding-left: 0px;

        .autocomplete-item {
            text-decoration: none;
            list-style: none;
            padding: 7px;
            border-bottom: 1px solid #ccc;

            &.active {
                background: #f65b5b62;
                cursor: pointer;
                font-weight: 500;
            }

            &:hover {
            //   @extend .autocomplete-item.active;
            }

            &:last-child {
                border:  none;
            }

            span {
                margin-left: 10px;
            }

        }

    }


</style>