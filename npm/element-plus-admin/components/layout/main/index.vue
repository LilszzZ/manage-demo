<template>
  <div class="c-main">
    <div class="c-main__body">
      <router-view />
    </div>
    <el-breadcrumb class="c-main__breadcrumb" separator="/">
      <template v-if="menus[0].title">
        <el-breadcrumb-item>{{ menus[0].title }}</el-breadcrumb-item>
        <el-breadcrumb-item :to-route="menus[2].title ? menus[1].path : ''">
          {{ menus[1].title }}
        </el-breadcrumb-item>
        <el-breadcrumb-item v-if="$route.query.$menu1Title">
          {{ $route.query.$menu1Title }}
        </el-breadcrumb-item>
        <el-breadcrumb-item
          v-if="menus[2].title"
          :to-route="menus[3].title ? menus[2].route : ''"
        >
          {{ menus[2].title }}
        </el-breadcrumb-item>
        <el-breadcrumb-item v-if="$route.query.$menu2Title">
          {{ $route.query.$menu2Title }}
        </el-breadcrumb-item>
        <el-breadcrumb-item v-if="menus[3].title">
          {{ menus[3].title }}
        </el-breadcrumb-item>
      </template>
      <template v-else>
        <el-breadcrumb-item>首页</el-breadcrumb-item>
      </template>
    </el-breadcrumb>
  </div>
</template>

<script src="./script.js"></script>

<style lang="scss" src="./style.scss"></style>
