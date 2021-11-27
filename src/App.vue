<template>
  <div id="app">
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
    <!-- 显示的是当前路由地址对应的内容 -->
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
