<template>
    <div>
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item border-bottom" v-for="item of list" :key="item.id">
                <div class="item-img-wrapper">
                    <img class="item-img" :src="item.imgUrl" alt="">
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
    
</template>

<script>
export default {
    name: 'HomeWeekend',
    props: {
        list: Array
    }
}
</script>

<style scoped>
    .title {
        line-height: .8rem;
        background: #eee;
        text-indent: .2rem;
    }
    /* .item {
        display: flex;
        height: 1.9rem;
        overflow: hidden;
        border-bottom: solid 1px #bdbaba;
    } */
    .item-img-wrapper {
        overflow: hidden;
        height: 0;
        padding-bottom: 37.09%;
    }
    .item-img-wrapper img {
        width: 100%;
    }
    /* .item .item-img {
        width: 1.7rem;
        height: 1.7rem;
        padding: .1rem;
    } */
    .item .item-info {
        padding: .1rem;
              /*这样可以让...出来*/
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

</style>