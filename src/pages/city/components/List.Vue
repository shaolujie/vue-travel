<template>
    <div class="List" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.currentCity}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div @click="handleCityClick(item.name)" class="button-wrapper" v-for="item of hot" :key="item.id"> 
                        <div class="button">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div class="item" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
                </div>
            </div>
        </div>
    </div>
  </template>
<script>
    import Bscoll from 'better-scroll'
    import { mapState, mapMutations } from 'vuex'
    export default {
        name: 'CityList',
        props: {
            hot: Array,
            cities: Object,
            letter: String
        },
        computed: {
            ...mapState({
                currentCity: 'city'
            })
        },
        updated() {
            this.scroll = new Bscoll(this.$refs.wrapper, {
                click: true
            });
        },
        methods: {
            handleCityClick (city) {
                this.changeCity(city)
                this.$router.push('/')
            },
            ...mapMutations(['changeCity'])
        },
        watch: {
            letter() {
                if(this.letter) {
                    const element = this.$refs[this.letter][0];
                    this.scroll.scrollToElement(element);
                }
            }
        }
    }
</script>

<style scoped>
    .List {
        position: absolute;
        top: 1.58rem;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: hidden;
    }
    .title {
        line-height: .54rem;
        background: #eee;
        padding-left: .2rem;
        color: #666;
        font-size: .26rem;
    }
    .button-list {
        overflow: hidden; /*开启bfc，不然下方的float无用*/
        padding: .1rem .6rem .1rem .1rem ;
    }
    .button-list .button-wrapper {
        float: left;
        width: 33%;
    }
    .button-list .button {
        margin: .1rem;
        padding: .1rem 0;
        text-align: center;
        border: .02rem solid #ccc;
        border-radius: .06rem;
    }
    .item-list .item {
        line-height: .76rem;
        color: #666;
        padding-left: .2rem;
    }
</style>