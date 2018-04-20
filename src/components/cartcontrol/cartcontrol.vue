<template>
    <div class="cartcontrol">
        <transition name="fade">
            <div class="cart-decrease" @click="decreaseCart()" v-show="food.count > 0">
                <transition name="inner">
                    <span class="inner icon-tx"></span>
                </transition>
            </div>
        </transition>
        <div class="cart-count" v-show="food.count">{{food.count}}</div>
        <div class="cart-add icon-gift" @click="addCart()"></div>
    </div>
</template>

<script type="text/ecmascript-6">
    import Vue from 'vue'
    export default {
        props: {
            food: {
                type: Object
            }
        },
        methods: {
            addCart () {
                if (!this.food.count) {
                    Vue.set(this.food, 'count', 1)
                } else {
                    this.food.count++
                }
            },
            decreaseCart () {
                if (this.food.count) {
                    this.food.count--
                }
            }
        }
    }
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .cartcontrol
        font-size: 0
        .cart-decrease
            display: inline-block
            padding: 6px
            transition: all .5s linear
            &.fade-leave-active
                transition: all .5s linear
            &.fade-enter,&.fade-leave-active
                opacity: 0
                transform: translate3d(24px, 0, 0)
            &.inner
                display: inline-block
                font-size: 24px
                line-height: 24px
                color: rgb(0, 160, 220)
            &.inner-enter-active,&.inner-leave-active
                transition: all .5s linear
                transform: rotate(0)
            &.inner-enter,&.inner-leave-active
                opacity: 0
                transform: rotate(180)
        .cart-count
            display: inline-block
            vertical-align: top
            width: 12px
            padding-top: 6px
            line-height: 24px
            text-align: center
            font-size: 10px
            color: rgb(147, 153, 159)
        .cart-add
            display: inline-block
            padding: 6px
            font-size: 24px
            line-height: 24px
            color: rgb(0, 160, 220)
</style>
