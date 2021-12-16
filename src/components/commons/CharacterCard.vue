<template>
    <div class="character text-center">
        <img class="mb-3" :src="info.image" :alt="info.name">
        <h4>{{info.name}}</h4>
        <hr>
        <p>{{info.origin}}</p>
        <p><strong>{{info.gender}}</strong></p>
    </div>
</template>

<script>
export default {
    name: 'CharacterCard',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
    img {
        width: 100%;
        border-radius: 50%;
        box-shadow: 0px 0px 15px #aaa;
    }

    hr {
        width: 60px;
        margin-left: auto;
        margin-right: auto;
        opacity: 1;
    }
</style>