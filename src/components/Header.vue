<template>
  <el-header class="header">
    <el-menu :default-active="index"
            router mode="horizontal">
      <el-menu-item index="/">Home</el-menu-item>
      <el-menu-item index="/write">글 작성</el-menu-item>
    </el-menu>
  </el-header>
</template>

<script setup lang="ts"></script>

<style scoped>
.header {
    padding: 0;
    height: 60px;
    
    el-menu-item {
      background-color: #5FFFCC;
      text-decoration: none;
    }
}
</style>