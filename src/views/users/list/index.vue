<template>
  <c-list
    :total="list.total"
    :current-page="currentPage"
    @page-change="onPageChange"
  >
    <template #operations>
      <el-button type="primary" @click="reRender">刷新</el-button>
    </template>
    <template #filters>
      <el-form
        :ref="cFilters.ref"
        :model="cFilters.model"
        :rules="cFilters.rules"
        inline
      >
        <el-form-item prop="name">
          <el-input
            clearable
            placeholder="请输入用户昵称"
            v-model.trim="cFilters.model.nickName.$like"
          />
        </el-form-item>
        <el-form-item prop="phoneNumber">
          <el-input
            clearable
            placeholder="请输入手机号"
            v-model.trim="cFilters.model.phoneNumber.$like"
          />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="search">查询</el-button>
        </el-form-item>
      </el-form>
    </template>
    <el-table :data="list.items" stripe>
      <el-table-column label="用户头像" width="120">
        <template #default="{ row }">
          <c-list-image :src="row.wxAvatarUrl" />
        </template>
      </el-table-column>
      <el-table-column prop="nickName" label="用户昵称" />
      <el-table-column prop="phoneNumber" label="手机号" width="140" />
      <el-table-column label="性别" width="80">
        <template #default="{ row }">
          {{ $helpers.getItem(enums.Gender, "value", row.gender)["label"] }}
        </template>
      </el-table-column>
    </el-table>
  </c-list>
</template>

<script src="./script.js"></script>
