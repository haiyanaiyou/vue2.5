<template>
    <div>
        <router-link to="/" tag="div" v-show="showAbs">
            <div class="header-abs">
                <span class="iconfont back-icon">&#xe624;</span>
            </div>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
                <span class="iconfont header-back-icon">&#xe624;</span>
            </router-link>
            <div>景点详情</div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            showAbs: true,
            opacityStyle:{
                opacity:0
            }
        }
    },
    methods:{
        handleScroll: function(){
            const top = document.documentElement.scrollTop;
            if(top > 60){
                let opacity = top/140;
                opacity > 1 ? 1: opacity;
                this.opacityStyle={ opacity};
                this.showAbs = false;
            }else{
                this.showAbs = true;
            }
            
        }
    },
    activated(){
        window.addEventListener('scroll',this.handleScroll)
    },
    deactivated(){
        //页面即将被隐藏的时候使用
        window.removeEventListener('scroll',this.handleScroll);
    }
}
</script>

<style lang="stylus" scoped>
@import '~style/varibles.styl'
    .header-abs
        position absolute
        top .2rem
        left .2rem
        width .8rem
        height .8rem
        line-height .8rem
        text-align center
        border-radius .4rem
        background rgba(0,0,0, .8)
        .back-icon
            color #fff
    .header-fixed
        overflow hidden
        height .86rem
        line-height  .86rem
        background $bgColor
        color #ffffff
        text-align center
        position fixed
        z-index 2
        top 0
        left 0
        right 0
        .header-back-icon
            position absolute
            top 0
            left .2rem
            color #ffffff
</style>