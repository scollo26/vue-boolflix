<template>
<div class="col">
    <div class="card-item">
        <div class="cont-img">
            <img class="img " v-if="noPhoto" :src="image" :alt="title">
            <!-- <img v-else src="https://cdn.download.it/ms/static/images/poster-placeholder.png" :alt="title"> -->
            <img class="no-film" v-else src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyRDytPc4c7g7Trm5EUutIQVGxwvEKA41hUg&usqp=CAU" :alt="title">
        </div>
        <div class="info-hover p-3">
            <div class="info">
                <div>{{title}}</div> 
            <div>{{original}}</div>
        
            <div>
                <i :class="'flag flag-' + getFlags(lang)"> </i>
            </div>
            <div> <i
                v-for="star in 5"
                :key="star"
                :class="(star <= transfNum(vote)) ? 'fas fa-star' : 'far fa-star'"
                />   
            </div> 
            <span>Trama{{(overview != "") ? overview : 'nessuna descrizione'}}</span>
            <div>{{transfNum(vote)}}</div>  

            </div>
            
        </div>  
    </div>
</div>

</template>

<script>
export default {
    name:"Card",
    props: [
        'title',
        'image',
        'original',
        'lang',
        'vote',
        'noPhoto',
        'overview',
    ],
    data() {
        return {         
        }
    },
    methods: {
        getFlags(lang){
            switch (lang){
                case 'en':
                    return 'uk';
                case 'ko':
                    return 'kr';
                case 'ja':
                    return 'jp';
                case 'ur':
                    return 'pk';
                case 'zh':
                    return 'cn';
                default:
                    return lang;
            }
        },
        transfNum(vote){

        const numberStar = vote / 2;
        return Math.round(numberStar)
        }
    }
    

}
</script>

<style lang="scss" >
.col {
    padding: 1em;
    .card-item {
        position: relative;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        // border: 1px solid white;
        width: 14em;
        .cont-img {
            height: 100%;
            width: 14em;
            overflow: hidden;
        img {
            width: 100%;
        }
        .no-film{
            height: 336px;
        }
        }
    }
}



</style>