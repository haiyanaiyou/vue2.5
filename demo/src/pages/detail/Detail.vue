<template>
    <div>
        <banner 
            :sightName="sightName" 
            :bannerImg="bannerImg"
            :bannerImgs="gallaryImgs"
        ></banner>
        <detail-header></detail-header>
        <detail-list  :list='list'></detail-list>
        <div class="content"></div>
        
    </div>
</template>

<script>
import Banner from './components/Banner.vue'
import DetailHeader from './components/Header.vue'
import DetailList from './components/List.vue'
import axios from 'axios'
export default {
    name:'Detail',
    components:{ Banner, DetailHeader, DetailList},
    data(){
        return{
            sightName: '',
            bannerImg:'',
            gallaryImgs:[],
            list:[]
                
        }
    },
    mounted(){
        this.getDetailInfo();
    },
    methods:{
        getDetailInfo(){
            axios.get('/api/detail.json',{
                params:{
                    id: this.$route.params.id
                }
            }).then(this.handleGetDetail)
        },
        handleGetDetail(res){
            res = res.data;
            if(res.ret && res.data){
                const data = res.data;
                this.sightName = data.sightName;
                this.bannerImg = data.bannerImg;
                this.gallaryImgs = data.gallaryImgs;
                this.list = data.categoryList;
            }

        }
    }
    
    
}
</script>

<style lang="stylus" scoped>
    .content
        height 50rem
</style>