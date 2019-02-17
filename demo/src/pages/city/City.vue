<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :hot="hotCities" :cities="cities" :letter='letter'></city-list>
        <city-alphabet :cities="cities" @change="handleClickChange"></city-alphabet>
    </div>
</template>

<script>
import axios from 'axios';
import CityHeader from './components/Header.vue';
import CitySearch from './components/Search.vue';
import CityList from './components/List.vue';
import CityAlphabet from './components/Alphabet.vue';
export default {
    components:{CityHeader, CitySearch, CityList, CityAlphabet},
    data(){
        return{
            cities:{},
            hotCities:[],
            letter: ''
        }
    },
    mounted () {
        this.getCityData();
    },
    methods: {
        getCityData: function(){
            axios.get('/api/city.json').then(this.setCityData)
        },
        setCityData: function(res){
           const data = res.data;
            if(data.ret && data.data){
                this.cities = data.data.cities;
                this.hotCities = data.data.hotCities;

            }
        },
        handleClickChange:function(letter){
            this.letter = letter;
        }
    },
}
</script>

<style lang="stylus" scoped>
    
</style>