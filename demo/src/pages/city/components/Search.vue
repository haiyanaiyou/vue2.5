<template>
    <div>
        <div class="search">
            <input v-model="keyword" type="text" class="search-input" placeholder="请输入城市名称或者拼音"/>
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul>
                <li class="search-item border-bottom" 
                    v-for="item of list" 
                    :key="item.id"
                    @click="handleClick(item.name)"
                    >{{item.name}}</li>
                <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配的数据</li>
            </ul>
        </div>
    </div>
    
</template>

<script>
import BScroll from 'better-scroll'
export default {
    props:{
        cities: Object
    },
    data(){
        return{
            timer: null,
            keyword: '',
            list:[]
        }
    },
    computed: {
       hasNoData: function(){
           return !this.list.length
       } 
    },
    mounted() {
        this.scroll = new BScroll(this.$refs.search);
    },
    watch: {
        keyword:function(){
            if(this.timer){
                clearTimeout(this.timer)
            }
            if(!this.keyword){
                this.list = [];
                return
            }
            this.timer = setTimeout(()=>{
                const result = [];
                for(let i in this.cities){
                    this.cities[i].forEach((value) => {
                        if(value.spell.indexOf(this.keyword) > -1 ||value.name.indexOf(this.keyword)> -1){
                            result.push(value)
                        }
                    });
                }
                this.list = result;
            },100)
        }
    },
    methods: {
        handleClick(city){
            this.$store.dispatch('changeCity',city);
            this.$router.push('/');
        }
    },
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .search
        height .72rem
        padding 0 .1rem
        background $bgColor
        .search-input
            height .62rem
            line-height .62rem
            width 100%
            box-sizing border-box
            padding 0 .1rem
            color #666
            border-radius .06rem
            text-align center
    .search-content
        z-index 1
        position absolute
        top 1.62rem
        bottom 0
        left 0
        right 0
        background #eee  
        .search-item
            line-height .62rem
            color #666
            padding-left .2rem
            background #fff
</style>