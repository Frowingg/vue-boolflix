<template>
    <div class="card">
        <div v-show="hover === false" class="poster">
            <img @mouseenter="invertHover()" v-if="item.poster_path !== null" :src="'https://image.tmdb.org/t/p/w342/'+item.poster_path" alt='img'>
            <img id="unav" v-else src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.XNvuzJaugn7Pn_pJopV2RQAAAA%26pid%3DApi&f=1.jpg" alt="img">
        </div>
        <div @mouseleave="invertHover()" v-show="hover === true" class="txts">
            <div class=txt>Titolo: {{item.title}}</div>
            <div class=txt>Titolo originale: {{item.original_title}}</div>
            <div class=txt>Voto:</div>
            <div class="txt stars">
                <span v-for="i in changeVote" :key="i">
                    <i  class="fa-solid fa-star"></i>
                </span>
                <span v-for="i in 5-changeVote" :key="i">
                    <i  class="fa-regular fa-star"></i>
                </span>  
            </div>
            <div class=txt>Lingua: <flag :iso=item.original_language /> </div>            
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComponentMovie',
    props: {
        'item': Object
    },
    computed: {
        changeVote() {
            return Math.round(this.item.vote_average/2);
        },
    },
    data() {
        return {
            hover: false,
        }
    },
    methods: {
        invertHover() {
            this.hover = !this.hover;
        }
    }
}
</script>

<style lang="scss" scoped>
img{
    height: 100%;
}
.card{
    color: white;
    min-width: 186px;
    .txt{
        margin: 5px 0;
    }
    i{
        color: yellow;
    }
    .poster{
        height: 100%;
        overflow: hidden;

        img{
            height: 100%;
        }
    }
    .txts{
        width: 140px;
        height: 100%;
        border: 1px solid white;
        padding: 10px;
        min-width: 186px;
    }

}


</style>