<template>
    <section class="container">
        <div class="row mb-5">
            <div class="col">
                <SearchBar @search="searchCharacters"/>
            </div>
        </div>
        <div v-if="characters != null" class="row">
            <div class="col-12 col-sm-6 col-lg-3 mb-4" v-for="(character, index) in charactersFiltered" :key="index">
                <CharacterCard :info="character"/>
            </div>
        </div>
        <div v-else class="loader">
            Loader
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import CharacterCard from '../commons/CharacterCard.vue';
import SearchBar from '../commons/SearchBar.vue';

export default {
    name: 'CharactersList',
    components: {
        CharacterCard,
        SearchBar
    },
    data() {
        return {
            characters: null,
            searchText: ""
        }
    },
    created() {
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
        .then((response) => {
            // handle success
            this.characters = response.data;
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
    },
    methods: {
        searchCharacters(payload) {
            this.searchText = payload;
        }
    },
    computed: {
        charactersFiltered() {
            const arrayFiltered = this.characters.filter( (elm) => {
                return elm.name.toLowerCase().includes(this.searchText.toLowerCase()); // true o false
            } );  // se è true mantengo il personaggio altrimenti lo scarto

            return arrayFiltered;
        }
    }
}
</script>

<style>

</style>