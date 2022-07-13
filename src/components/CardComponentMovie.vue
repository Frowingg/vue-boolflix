<template>
    <li>
        <img :src="'https://image.tmdb.org/t/p/w92/'+item.poster_path" alt='img'>
        <div>Titolo: {{item.title}}</div>
        <div>Titolo originale: {{item.original_title}}</div>
        <div>Lingua: <flag :iso=item.original_language /> </div>
        <div>Voto:{{changeVote}}</div>
    </li>
</template>

<script>
export default {
    name: 'CardComponentMovie',
    props: {
        'item': Object
    },
    computed: {
        changeVote() {
            if (this.item.vote_average < 5) {
                return Math.ceil(this.item.vote_average)
            } else {
                return Math.ceil(this.item.vote_average)-5
            }
        }
    }
}
</script>

<style>

</style>