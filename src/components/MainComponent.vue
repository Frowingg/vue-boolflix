<template>
  <main>
    <h2>Film</h2>
    <section class="items" v-if="movieCards.length">

        <CardComponentMovie class="card"
        v-for="cardMovie in movieCards"
        :key="cardMovie.id"
        :item="cardMovie"
        />

    </section>  

    <h2>Serie TV</h2>
    <section class="items" v-if="serieCards.length">   

        <CardComponentSerie class="card"
        v-for="cardSerie in serieCards"
        :key="cardSerie.id"
        :item="cardSerie"
        />

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

<style lang="scss" scoped>
main{
    height: calc(100vh - 60px);
    background-color: #434343;
    overflow-y: scroll;
    padding: 0 30px;
}
h2{
    margin: 5px 0;
    color: white;
}
ul{
    list-style-type: none;
}
.items{
    margin: 0 auto;
    height: calc(50% - 40px);
    width: 99%;
    overflow: auto;
    display:flex;
}
.card{
    width: 140px;
    height: 95%;
    background-color: black;
    margin-right: 10px;
}

</style>