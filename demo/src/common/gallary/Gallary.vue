<template>
    <div class="container" @click="hide" v-if="isShowGallary">
        <div class="wrapper">
            <swiper :options="swiperOption">
                <swiper-slide v-for="item of imgs" :key="item">
                    <img class="swiper-img" :src="item" alt="" srcset="" />
                </swiper-slide>
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
export default {
    name:'DetailGallary',
    props:{
        imgs:{
            type: Array,
            default(){
                return ['http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_r_800x800_d6a63068.jpg','http://img1.qunarzz.com/sight/p0/1811/d5/d5153b5e337c0644a3.water.jpg_r_800x800_5785f05e.jpg']
            }
        }
    },
    data(){
        return{
            swiperOption:{
               pagination: {
                    el: '.swiper-pagination',
                    type: 'fraction'
                },
                observer:true,
                observeParents:true
            },
            isShowGallary: false
        }
    },
    methods:{
        show(){
            this.isShowGallary = true;
        },
        hide(){
            // this.$nextTick(() => {
            //     this.isShowGallary = false;
            // })
            setTimeout(() => {
                this.isShowGallary = false;
            });
        }
    },
    mounted() {
        window.vm = this;
    },
}
</script>

<style lang="stylus" scoped>
    .container >>> .swiper-container
        overflow inherit
    .container
        display flex
        flex-direction column
        justify-content center
        position fixed
        z-index 99
        left 0
        right 0
        top 0
        bottom 0
        background #000
        .wrapper
            height 0
            width 100%
            padding-bottom 100%
            .swiper-img
                width 100%
            .swiper-pagination
                color #ffffff
                bottom -1rem
</style>