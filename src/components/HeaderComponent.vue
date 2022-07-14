<template>
    <header>
        <h1>Boolflix</h1>
        <div>
            <input 
            v-model="inputText"
            type="text"
            placeholder="Cerca il film"
            @keyup="$emit('performeSearch', inputText)"
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
            inputText: 'ciao'
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
input, button{
    background-color: #434343;
    border: 1px solid red;
    padding: 5px 10px; 
    border-radius: 25px;
    color: white;
}
input:focus{
    border:1px solid red;
} 
</style>