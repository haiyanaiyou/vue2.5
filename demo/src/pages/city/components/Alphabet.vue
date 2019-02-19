<template>
    <ul class="list" >
        <li class="item" 
            v-for="item of letters" 
            :key="item"
            :ref="item"
            @touchstart.prevent="handleTouchStart"
            @touchmove="handleTouchMove"
            @touchend="handleTouchEnd"
            @click="handleLetterClick"
        >{{item}}</li>
    </ul>
</template>

<script>
export default {
    props:{
        cities: Object
    },
    data(){
        return{
            touchStart: false,
            startY: '',
            timer: null
        }
    },
    computed: {
        letters:function(){
            const letters =[];
            for(let i in this.cities){
                letters.push(i)
            }
            return letters
        }
    },
    updated() {
        this.startY = this.$refs['A'][0].offsetTop;
    },
    methods: {
        handleLetterClick:function(e){
            this.$emit('change',e.target.innerText);
        },
        handleTouchStart:function(){
            this.touchStart = true;
        },
        handleTouchMove: function(e){
            if(this.touchStart){
                if(this.timer){
                    clearTimeout(this.timer);
                }
                this.timer = setTimeout(()=>{
                    const touchY = e.touches[0].clientY -79;
                    const index = Math.floor((touchY-this.startY)/20);
                    if(index >= 0 && index< this.letters.length){
                        this.$emit('change',this.letters[index]);
                    }
                },16)
                
            }
        },
        handleTouchEnd: function(){
            this.touchStart = false;
        }
    },
}
</script>

<style lang="stylus" scoped>
   @import '~style/varibles.styl' 
   .list 
        position absolute
        right 0
        top 1.68rem
        bottom 0
        width .4rem
        display flex
        flex-direction column
        justify-content center
    .item
        line-height  .4rem
        color $bgColor
        text-align center

</style>