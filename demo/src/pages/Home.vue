<template>
    <div>
        <v-header></v-header>
        <v-swiper :list='swiperList'></v-swiper>
        <v-icon :icon='icons'></v-icon>
        <v-recomment :list="recommentList"></v-recomment>
        <v-weekend :list='weekendList'></v-weekend>
    </div>
</template>

<script>
import VHeader from './../components/Header.vue'
import VSwiper from '@/components/Swiper.vue'
import VIcon from '@/components/Icon.vue'
import VRecomment from '@/components/Recomment.vue'
import VWeekend from '@/components/Weekend.vue'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
    components:{ VHeader, VSwiper, VIcon, VRecomment, VWeekend },
    data(){
        return{
            lastCity: '',
            swiperList:[],
            icons:[],
            recommentList:[],
            weekendList:[]

        }
    },
    mounted () {
        this.lastCity = this.city;
        this.getHomeInfo();
        
    },
    computed:{
        ...mapState(['city'])
    },
    activated(){
        if(this.lastCity !== this.city){
            this.lastCity = this.city;
            this.getHomeInfo();
        }
    },
    methods:{
        getHomeInfo: function(){
            axios.get('/api/index.json?city='+ this.city)
            .then(this.getHomeInfoData)
        },
        getHomeInfoData: function(res){
            res = res.data;
            if(res.ret && res.data){
                this.swiperList = res.data.swiperList;
                this.icons = res.data.iconList;
                this.recommentList = res.data.recommendList;
                this.weekendList = res.data.weekendList;

            }
        }
    }
    
}
</script>

<style scoped>

</style>

