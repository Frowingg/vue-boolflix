<template>
    <div>
        <li>
            <img :src="'https://image.tmdb.org/t/p/w92/'+item.poster_path" alt="img">
            <div>Titolo: {{item.name}}</div>
            <div>Titolo originale: {{item.original_name}}</div>
            <div>Lingua: <flag :iso=item.original_language /></div>
            <div>Voto: {{changeVote}}</div>
        </li>
    </div>
</template>

<script>
export default {
    name: 'CardComponentSerie',
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