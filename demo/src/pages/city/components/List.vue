<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.city}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wrapper" 
                        v-for="item of hot" 
                        :key="item.id"
                        @click="handleClick(item.name)"
                        >
                        <div class="button">{{item.name}}</div>
                    </div>  
                </div>
            </div>
            <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom" >{{key}}</div>
                <div class="item-list" 
                    v-for="innerItem of item" 
                    :key="innerItem.id"
                     @click="handleClick(innerItem.name)">
                    <div class="item border-bottom" >{{innerItem.name}}</div>
                   
                </div>
            </div>
           
        </div>
        
    </div>
</template>

<script>
import BScroll from 'better-scroll';
import {mapState} from 'vuex';
export default {
    props:{
        cities: Object,
        hot: Array,
        letter: String
    },
    data(){
        return{

        }
    },
    mounted() {
        this.srcoll = new BScroll(this.$refs.wrapper)
    },
    watch: {
        letter:function(){
            if(this.letter){
                const element = this.$refs[this.letter][0];
                this.srcoll.scrollToElement(element);
            }
        }
    },
    methods: {
        handleClick(city){
            this.$store.commit('changeCity',city);
            this.$router.push('/');
        }
    },
    computed:{
        ...mapState(['city'])
    }
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .border-topbottom
        &:before 
            border-color #cccccc
        &:after 
            border-color #cccccc
    .border-bottom
        &:before 
            border-color #cccccc
        &:after 
            border-color #cccccc
    .list
        position absolute
        top 1.62rem
        left 0
        bottom 0
        right 0
        overflow hidden
        .title
            line-height .54rem
            background #eeeeee
            padding-left .2rem
            color #333
            font-size .26rem
        .button-list
            overflow hidden
            padding .1rem .6rem .1rem .1rem
            .button-wrapper
                width 33.33%
                float left
                .button
                    padding .1rem 0
                    border .02rem solid #ccc
                    margin .1rem
                    text-align center
                    border-radius .06rem
        .item-list
            .item
                line-height .76rem
                padding-left .22rem
</style>