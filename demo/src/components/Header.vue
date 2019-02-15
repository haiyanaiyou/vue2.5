<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont">&#xe624;</span>
        </div>
        <div class="header-input">
            输入城市/景点/游玩主题
        </div>
        <div class="header-right">城市</div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            
        }
    }
}
</script>

<style lang="stylus" scoped>
     .header
        display: flex
        line-height: 0.86rem
        background: #00bcd4
        color:#fff

        .header-left
            width:0.64rem
            float:left
        .header-input
            flex:1
            background : #ffffff
            border-radius : .1rem
            margin-top : .12rem
            height : .64rem
            line-height : .64rem
            color: #ccc
            margin-left: .2rem
        .header-right
            width: 1.24rem
            float: right
            text-align: center

</style>