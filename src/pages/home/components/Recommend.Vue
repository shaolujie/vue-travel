<template>
    <div>
        <div class="title">热销推荐</div>
        <ul>
            <!-- <router-link to="/detail">
                <li class="item border-bottom" v-for="item of list" :key="item.id">
                    <img class="item-img" :src="item.imgUrl" alt="">
                    <div class="item-info">
                        <p class="item-title">{{item.title}}</p>
                        <p class="item-desc">{{item.desc}}</p>
                        <button class="item-button">查看详情</button>
                    </div>
                </li>
            </router-link> -->
            <router-link :to="'/detail/' + item.id" tag="li" class="item border-bottom" v-for="item of list" :key="item.id">
                <img class="item-img" :src="item.imgUrl" alt="">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </router-link>
        </ul>
    </div>
    
</template>

<script>
export default {
    name: 'HomeRecommend',
    props: {
        list: Array
    }
}
</script>

<style scoped>
    .title {
        margin-top: .2rem;
        line-height: .8rem;
        background: #eee;
        text-indent: .2rem;
    }
    .item {
        display: flex;
        height: 1.9rem;
        overflow: hidden;
        border-bottom: solid 1px #bdbaba;
    }
    .item .item-img {
        width: 1.7rem;
        height: 1.7rem;
        padding: .1rem;
    }
    .item .item-info {
        flex: 1;
        padding: .1rem;
        min-width: 0;       /*这样可以让...出来*/
    }
    .item .item-title {
        line-height: .54rem;
        font-size: .32rem;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }
    .item .item-desc {
        line-height: .4rem;
        color: #ccc;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }
    .item .item-button {
        background: .2rem;
        background: #ff9300;
        padding: 0 .2rem;
        border-radius: .06rem;
        color: #fff;
    }
</style>