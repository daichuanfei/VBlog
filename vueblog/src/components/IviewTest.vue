<template>
    <Card style="width:350px">
        <p slot="title">
            <Icon type="ios-film-outline"></Icon>
            Classic film
        </p>
        <a href="www.baidu.com" slot="extra" @click.prevent="changeLimit">
            <Icon type="ios-loop-strong"></Icon>
            Change
        </a>
        <ul>
            <p v-for="(item, index) in randomMovieList" :key="index">
                <a :href="item.url" target="_blank">{{item.name}}</a>
                <Button type="primary">按钮</Button>
                <span>
                    <Icon type="ios-star" v-for="n in 4" :key="n"></Icon>
                    <Icon type="ios-star" v-if="item.rate>=9.5"></Icon><Icon type="ios-star-half" v-else>></Icon>
                    {{item.rate}}
                </span>
            </p>
        </ul>
    </Card>
</template>
<script>
export default {
    data(){
        return{
            movieList:[{
                name:'The Shawshank Redemption',
                url:'https://movie.douban.com/subject/1292052/',
                rete:9.6
            },{
                name:'Leon:The Professiona',
                url:'https://movie.douban.com/subject/1295644/',
                rate:9.4
            },{
                name:'Farewell to My Concubine',
                url: 'https://movie.douban.com/subject/1291546/',
                rate:9.4
            },{
                name: 'Forrest Gump',
                url: 'https://movie.douban.com/subject/1292720/',
                rate: 9.4
            },{
                name: 'Life Is Beautiful',
                url: 'https://movie.douban.com/subject/1292063/',
                rate: 9.5
            },{
                name: 'Spirited Away',
                url: 'https://movie.douban.com/subject/1291561/',
                rate: 9.2
            },{
                name: 'Schindler\'s List',
                url: 'https://movie.douban.com/subject/1295124/',
                rate: 9.4
            },{
                name: 'The Legend of 1900',
                url: 'https://movie.douban.com/subject/1292001/',
                rate: 9.2
            },{
                name: 'WALL·E',
                url: 'https://movie.douban.com/subject/2131459/',
                rate: 9.3
            },{
                name: 'Inception',
                url: 'https://movie.douban.com/subject/3541415/',
                rate: 9.2
            }    
            ],
            randomMovieList:[]
        }
    },
    methods:{
        changeLimit(){
            function getArrayItems(arr,num){
                const temp_arr=[];
                for (let index in arr){
                    temp_arr.push(arr[index]);
                }
                const return_arr=[];
                for(let i=0;i<num;i++){
                    if(temp_arr.length>0){
                        const arrIndex = Math.floor(Math.random()*temp_arr.length);
                        return_arr[i]=temp_arr[arrIndex];
                        temp_arr.splice(arrIndex,1);
                    }else{
                        break;
                    }
                }
                return return_arr;
            }
            this.randomMovieList = getArrayItems(this.movieList, 5);
        }
        
    },
    mounted(){
        this.changeLimit();
    }

}
</script>
<style>
li {
    display: list-item
}
</style>



