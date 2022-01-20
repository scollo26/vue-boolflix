<template>
<ul>
    <li>          
        <img class="img "
            :src="image"
            :alt="title">
        <div>{{title}}</div> 
        <div>{{original}}</div>
        <div>
            <i :class="'flag flag-' + getFlags(lang)">  
            </i>
        </div>
        <div>{{transfNum(vote)}}</div>    
    </li>
</ul>
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
        return numberStar.toFixed(0)
        }
    }
    

}
</script>

<style lang="scss" >

  
  
  ul{
      display: inline-block;
    list-style: none;
    margin: 0;
      li{
        
        border: 2px solid black;
        padding: 3em;
        width: 50%;
        img{
            width: 100%;
        }
      }
  }
  
  



</style>