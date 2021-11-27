<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩/主题
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{this.city}}
                <span class="iconfont  arrow-icon">&#xe600;</span>
            </div>
        </router-link>
    </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
      ...mapState(['city'])
  }
}
</script>

<style scoped>
    .header {
        display: flex;
        line-height: .86rem;
        background: #00bcd4;
        color: #fff;
    }
    .header-left {
        width: .64rem;
        float: left;
    }
    .header-left .back-icon {
        text-align: center;
        font-size: .4rem;
    }
    .header-right {
        min-width: 1.04rem;
        padding: 0 0.1rem;
        float: right;
        text-align: center;
        color: #fff;
    }
    .header-right .arrow-icon {
        font-size: .24rem;
        margin-left: -.04rem;
    }
    .header-input {
        flex: 1;
        line-height: .64rem;
        background: #fff;
        height: .64rem;
        border-radius: .1rem;
        margin-top: .12rem;
        margin-left: .2rem;
        color: #ccc;
        padding-left: .2rem;
    }
</style>
