<template>
    <div class="header">
        <router-link to="/">
            <span class="iconfont back-icon">&#xe624;</span>
        </router-link>
        <div>城市选择</div>
        
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .header
        overflow hidden
        height .86rem
        line-height  .86rem
        background $bgColor
        color #ffffff
        text-align center
        position relative
        .back-icon
            position absolute
            top 0
            left .2rem
            color #ffffff
            
</style>