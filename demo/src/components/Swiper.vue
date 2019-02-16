<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwipper">
            <!-- slides -->
            <swiper-slide v-for="item of list" :key='item.id'>
                <img class="swiper-img" :src="item.imgUrl" alt="" srcset="" />
            </swiper-slide>
            
            <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
    
</template>

<script>
export default {
    props:{
        list: Array
    },
    data(){
        return{
            swiperOption:{
                loop : true,
                autoplay:true,
                pagination: {
                    el: '.swiper-pagination'
                }
            }, 
        }
    },
    computed: {
        showSwipper: function(){
            return this.list.length
        }
    },
    
}
</script>

<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
        background : #fff
    .wrapper
        width:100%
        overflow: hidden
        height :0
        padding-bottom:31.67%
        background: #eee
        .swiper-img
            width: 100%
</style>
