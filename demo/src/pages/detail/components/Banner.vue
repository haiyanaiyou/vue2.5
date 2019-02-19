<template>
    <div class="banner" @click="handleBannerClick">
        <img class="banner-img" :src="bannerImg" alt="" srcset="">
        <div class="banner-info">
            <div class="banner-title">{{this.sightName}}</div>
            <div class="banner-number">
                <span class="iconfont banner-icon">&#xe6dd;</span>
                {{this.bannerImgs.length}}
            </div>
        </div>
        <fade-animation>
            <detail-gallary
                ref="gallaryCpn" 
                :imgs="bannerImgs">
            </detail-gallary>
        </fade-animation>
        
    </div>
</template>

<script>
import DetailGallary from '@/common/gallary/Gallary.vue'
import FadeAnimation from '@/common/fade/Fade.vue'
export default {
   components:{DetailGallary, FadeAnimation },
   props:{
       sightName: String,
       bannerImg: String,
       bannerImgs: Array
   },
   data(){
        return{
            
        }
    },
    methods:{
        handleBannerClick(){
            this.$refs.gallaryCpn.show();
        }
    }
}
</script>

<style lang="stylus" scoped>
    .banner
        overflow hidden
        height 0
        padding-bottom 55%
        position relative
        .banner-img
            width 100%
        .banner-info
            color #fff
            position absolute
            left 0
            right 0
            bottom 0
            line-height .6rem
            background-image linear-gradient(top, rgba(0,0,0,0),rgba(0,0,0,.8))
            display flex
            .banner-title
                flex:1
                font-size .32rem
                padding 0 .2rem
            .banner-number
                padding 0 .1rem
                height .32rem
                line-height .32rem
                margin-top .14rem
                font-size .24rem
                border-radius .2rem
                background rgba(0,0,0,.8)
                .banner-icon
                    font-size .24rem
</style>