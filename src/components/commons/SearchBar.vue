<template>
    <div class="search-bar">
        <form class="d-flex">
            <input v-model="searchText" class="form-control" type="text" placeholder="Search character">
            <button class="btn btn-primary mx-3" @click.prevent="$emit('search',searchText)">Search</button>
            <button class="btn btn-warning" @click.prevent="$emit('search','')">Reset</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchText: ''
        }
    }
}
</script>

<style lang="scss" scoped>

</style>