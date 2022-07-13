<template>
    <li>
        <div>Titolo: {{item.name}}</div>
        <div>Titolo originale: {{item.original_name}}</div>
        <div>Lingua: <flag :iso=item.original_language /></div>
        <div>Voto: {{item.vote_average}}</div>
    </li>
</template>

<script>
export default {
    name: 'CardComponentSerie',
    props: {
        'item': Object
    } 
}
</script>

<style>

</style>