<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont back-icon">&#xe624;</span>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题
        </div>
        <div class="header-right">{{this.city}}
            <span class="iconfont arrow-icon">&#xe64a;</span>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            
        }
    },
    props:{city:String}
        
    
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
     .header
        display: flex
        line-height: 0.86rem
        background: $bgColor
        color:#fff

        .header-left
            width:0.64rem
            float:left
            .back-icon
                text-align: center
                font-size: 0.4rem
        .header-input
            flex:1
            background : #ffffff
            border-radius : .1rem
            margin-top : .12rem
            padding-left:.2rem
            height : .64rem
            line-height : .64rem
            color: #ccc
            margin-left: .2rem
        .header-right
            width: 1.24rem
            float: right
            text-align: center
            .arrow-icon
                font-size: .24rem
                margin-left : -.04rem

</style>