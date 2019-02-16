<template>
    <div>
        <v-header :city='city'></v-header>
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
export default {
    components:{ VHeader, VSwiper, VIcon, VRecomment, VWeekend },
    data(){
        return{
            city: '',
            swiperList:[],
            icons:[],
            recommentList:[],
            weekendList:[]

        }
    },
    mounted () {
        this.getHomeInfo()
    },
    methods:{
        getHomeInfo: function(){
            axios.get('/api/index.json').then(this.getHomeInfoData)
        },
        getHomeInfoData: function(res){
            res = res.data;
            if(res.ret && res.data){
                this.city = res.city;
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

