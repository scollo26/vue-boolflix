<template>
<div class="col">
    <!-- card-item hover sulla foto mostra le info -->
    <div class="card-item">
        <div class="cont-img">
            <!-- controllo se foto esiste prende dal server// se non esiste un'altra foto -->
            <img class="img " v-if="noPhoto" :src="image" :alt="title">
            <img class="no-film" v-else src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyRDytPc4c7g7Trm5EUutIQVGxwvEKA41hUg&usqp=CAU" :alt="title">
        </div>
        <!-- informazioni foto tutte nascoste -->
        <div class="info-hover p-3">
            <div class="info">
                <div>{{title}}</div> 
                <div>{{original}}</div>
                <div>
                    <i :class="'flag flag-' + getFlags(lang)"> </i>
                </div>
                <div><i
                    v-for="star in 5"
                    :key="star"
                    :class="(star <= transfNum(vote)) ? 'fas fa-star' : 'far fa-star'"
                    />   
                </div> 
                <span>Trama: {{(overview != "") ? overview : 'Nessuna descrizione'}}</span>
                <div>Voto: {{transfNum(vote)}}</div>  
            </div>
        </div>  
    </div>
</div>

</template>

<script>
export default {
    name:"Card",
    // variabili prese da array searchMovie in Main
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
        // switchper bandiere non esistenti dentro Api del server
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
        // funzione restituisce un numero intero per le stelle
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
            width: 100%;
            // width: 14em;
            overflow: hidden;
        img {
            width: 100%;
            height: 100%;
        }
        .no-film{
            height: 336px;
        }
    }
    .info-hover {
        
        position: absolute;
        background-color: black;
        color: white;
        opacity: 0.8;
        display: none;
        overflow: auto;
        cursor: pointer;
        height: 100%;
        .info {  
            display: block;
            text-align: center;
        }
    }
    
}
    .card-item:hover .info-hover {
        display: block;
        // width: 14em;
        width: 100%;
    }
    i{
        color: yellow;
    }
}



</style>