<template>
    <div class="container">
        <div class="row">
            <div class="col-12 col-sm-6 col-lg-3 mb-4" v-for="(character, index) in characters" :key="index">
                <CharacterCard :info="character"/>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import CharacterCard from '../commons/CharacterCard.vue';

export default {
    name: 'CharactersList',
    components: {
        CharacterCard
    },
    data() {
        return {
            characters: null
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
    }
}
</script>

<style>

</style>