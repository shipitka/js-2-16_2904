<template>
    <form action="#" class="search-form">
        <input type="text" class="search-field" v-model.trim='searchText'>
        <button class="btn-search" type="button" @click="searchGoods">
            <i class="fas fa-search"></i>
        </button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                searchText: ''
            }
        },
        methods: {
            searchGoods() {
                let request = this.searchText
                if (request === '') {
                    this.$parent.$refs.catalog.filteredGoods = this.$parent.$refs.catalog.unfilteredGoods;
                    this.$parent.searchFailed = false
                } else {
                    this.$parent.$refs.catalog.filteredGoods = this.$parent.$refs.catalog.unfilteredGoods.filter(goods => goods.product_name.toLowerCase() == request.toLowerCase());
                    if (this.$parent.$refs.catalog.filteredGoods.length == 0) {
                        this.$parent.searchFailed = true
                    } else {
                        this.$parent.searchFailed = false;
                    }
                };
            }
        }
    }
</script>

<style>

</style>