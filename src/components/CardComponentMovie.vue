<template>
    <li>
        <div>Titolo: {{item.title}}</div>
        <div>Titolo originale: {{item.original_title}}</div>
        <div>Lingua: <flag :iso=item.original_language /> </div>
        <div>Voto: {{item.vote_average}}</div>
    </li>
</template>

<script>
export default {
    name: 'CardComponentMovie',
    props: {
        'item': Object
    } 
}
</script>

<style>

</style>