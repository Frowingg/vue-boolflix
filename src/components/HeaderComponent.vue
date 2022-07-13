<template>
    <header>
        <h1>Boolflix</h1>

        <div>
            <input 
            v-model="inputText"
            type="text"
            placeholder="Cerca il film"
            >
            <button @click="$emit('performeSearch', inputText)">
                Cerca!
            </button>

        </div>

    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data: function() {
        return {
            inputText: ''
    }
    }
}
</script>

<style>
header{
    height: 60px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 30px;
}
h1{
    color: red;
}
</style>