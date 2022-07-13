<template>
  <main>
    <section v-if="movieCards.length">

        <ul>
            <CardComponentMovie class="card"
            v-for="cardMovie in movieCards"
            :key="cardMovie.id"
            :item="cardMovie"
            />
            
            <CardComponentSerie class="card"
            v-for="cardSerie in serieCards"
            :key="cardSerie.id"
            :item="cardSerie"
            />
        </ul>

    </section>
  </main>
</template>

<script>
import CardComponentMovie from './CardComponentMovie.vue';
import CardComponentSerie from './CardComponentSerie.vue';


export default {
    name: 'MainComponent',
    props: {
        'movieCards': Array,
        'serieCards': Array,
        'searching': Boolean
    },
    components: {
        CardComponentMovie,
        CardComponentSerie
    }
}
</script>

<style>
main{
    height: calc(100vh - 60px);
    background-color: #434343;
    padding: 50px;
    overflow-y: scroll;
}
ul{
    list-style-type: none;
    display: flex;
    flex-wrap: wrap;
}
.card{
    border: 1px solid white;
    margin: 30px;
    max-width: 250px;
    padding: 10px;
}
</style>