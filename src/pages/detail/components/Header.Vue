<template>
    <div>
        <router-link 
        tag="div" 
        to="/" 
        class="header-abs"
        v-show="showAbs"
        >
            <div class="iconfont header-abs-back">&#xe624;</div>
        </router-link>
        <div 
        class="header-fixed" 
        v-show="!showAbs"
        :style="opacityStyle"
        >
            <div class="iconfont header-fixed-back">&#xe624;</div>
            景点详情
        </div>
    </div>
    
</template>

<script>
export default {
    name: 'DetailHeader',
    data() {
        return {
            showAbs: true,
            opacityStyle: {
                opacity: 0
            }
        }
    },
    methods: {
        handleScroll () {
            const top = document.documentElement.scrollTop || document.body.scrollTop || window.pageYOffset
            if (top > 60 ) {
                let opacity = top / 140
                opacity = opacity > 1 ? 1 : opacity
                this.opacityStyle = {
                    opacity
                }
                this.showAbs = false
            } else {
                this.showAbs = true
            }
        }
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll, { passive: false })
    },
    destroyed() {
        window.removeEventListener('scroll', this.handleScroll, { passive: false })
    },
}
</script>

<style scoped>
.header-abs {
    position: absolute;
    left: .2rem;
    top: .2rem;
    width: .8rem;
    height: .8rem;
    border-radius: .4rem;
    text-align: center;
    line-height: .8rem;
    background: rgba(0, 0, 0, .8);
}
.header-abs-back {
    font-size: .4rem;
    color: #fff;
}
.header-fixed {
    z-index: 2;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        height: .86rem;
        line-height: .86rem;
        text-align: center;
        color: #fff;
        background: #00bcd4;
        font-size: .32rem;
    }
.header-fixed-back {
        position: absolute;
        top: 0;
        left: 0;
        width: .64rem;
        text-align: center;
        font-size: .4rem;
        color: #fff;
    }
</style>