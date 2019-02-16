<template>
    <div>
        <div class="recomment-title">热门推荐</div>
        <ul>
            <li class="item border-bottom" v-for="item of list" :key="item.id">
                <img :src="item.imgUrl" srcset="" class="item-img">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:{
        list:Array
    },
    data(){
        return{
           
        }
    }
}
</script>

<style lang="stylus" scoped>
@import '~style/mixin.styl'
    .recomment-title
        line-height: .8rem
        background: #eee
        margin-top:.2rem
        margin-bottom:.2rem
        text-indent:.2rem
    .item
        display:flex
        overflow:hidden
        height: 2.1rem
        .item-img
            width:1.7rem
            height: 1.7rem
            padding:.1rem
        .item-info
            flex:1
            padding: .1rem
            min-width:0
            .item-title
                font-size: .32rem
                line-height: .54rem
                ellipsis()
            .item-desc
                color: #ccc
                line-height: .4rem
                ellipsis()
            .item-button
                background: #ff9300
                padding: 0 .1rem
                line-height: .54rem
                color: #ffffff
                margin-top: .3rem
                border-radius: .06rem
</style>