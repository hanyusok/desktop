<script setup>
import DataView from './components/DataView.vue'
import MessageBoard from './components/MessageBoard.vue'
</script>

<template>
  <h2 class="hero-text">비대면 관리자</h2>
  <message-board></message-board>
  <data-view></data-view>
</template>

<style lang="less">
@import './assets/css/styles.less';
</style>
