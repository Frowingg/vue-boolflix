<template>
  <main>
    <section v-if="movieCards.length">

        <ul>
            <CardComponent class="card"
            v-for="card in movieCards"
            :key="card.id"
            :item="card"
            />
        </ul>

    </section>
  </main>
</template>

<script>
import CardComponent from './CardComponent.vue';

export default {
    name: 'MainComponent',
    props: {
        'movieCards': Array,
        'searching': Boolean
    },
    components: {
        CardComponent
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
}
</style>