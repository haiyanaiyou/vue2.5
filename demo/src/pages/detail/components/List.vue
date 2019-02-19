<template>
    <div>
        <div class="item border-bottom" v-for="(item, index) of list" :key="index">
            <div class="item-title">
                <span class="item-title-icon"></span>
                {{item.title}}
            </div> 
            <div v-if="item.children" class="item-children">
                <detail-list :list="item.children"></detail-list>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'DetailList',
    props:{
        list: Array
    }
}
</script>

<style lang="stylus" scoped>
    .item-title-icon
        display inline-block
        position relative
        top: 0.08rem
        left: 0.04rem
        width .36rem
        height .36rem
        margin-right .1rem
        background: url('http://s.qunarzz.com/piao/image/touch/sight/detail.png')  no-repeat 0 -.45rem
        background-size: .4rem 3rem;
    .item
        line-height .8rem
        padding 0 .2rem
    .item-children
        padding 0 .1rem
</style>