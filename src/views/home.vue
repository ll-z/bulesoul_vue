<template>
  <!--博文列表-->
  <el-row :gutter="12">
    <el-col :span="5">
      <!--分组-->
      <blogGroup :isEdit="false"/>
    </el-col>
    <el-col :span="18">
      <el-card shadow="hover"
               v-for="(item, index) in dataList"
               :key="'bloglist_' + index"
               >
        <template #header>
          <div class="card-header">
            <router-link :to="{params:{id:item.ID}}">
              {{item.title}}
            </router-link>
            <span class="button">({{dataFormat(item.addTime).format('YYYY-MM-DD')}})</span>
          </div>
        </template>
        <!--简介-->
        <div class="text item" v-html="item.introduction"></div>
        <hr>
        <i class="el-icon-view"></i> {{item.viewCount}}
        <i class="el-icon-circle-check"></i> {{item.agreeCount}}
        <i class="el-icon-chat-dot-square"></i> {{item.discussCount}}
      </el-card>
      <!--没有找到数据-->
      <el-empty description="没有找到博文呢" v-if="dataList.length === 0"></el-empty>
      <pafer/>
    </el-col>
  </el-row>

</template>

<script setup>
import {defineProps, watch} from 'vue'
// 路由，监听 params （props） 的变化
import {useRoute, onBeforeRouteUpdate} from 'vue-router'
// 组件

export default {
  name: "home"
}
</script>


<style scoped>

</style>
