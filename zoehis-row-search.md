# zoehis-row-search 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-row-search 是一个搜索行布局组件，将页面分为条件区域和按钮区域两部分，用于构建搜索条件区域。通常与 zoehis-row、zoehis-col、zoehis-col-item 配合使用。

## 基础用法

```vue
<template>
  <zoehis-row-search>
    <template slot="condition">
      <zoehis-row type="search" labelWidth="80px">
        <zoehis-col :span="8">
          <zoehis-col-item label="关键词">
            <el-input v-model="keyword" />
          </zoehis-col-item>
        </zoehis-col>
        <zoehis-col :span="8">
          <zoehis-col-item label="状态">
            <el-select v-model="status">
              <el-option label="启用" value="1" />
              <el-option label="禁用" value="0" />
            </el-select>
          </zoehis-col-item>
        </zoehis-col>
      </zoehis-row>
    </template>
    <template slot="button">
      <el-button type="primary" @click="handleSearch">查询</el-button>
      <el-button @click="handleReset">重置</el-button>
    </template>
  </zoehis-row-search>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| searchBtnClassName | String | '' | 自定义按钮组区域的 class 名称 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| condition | 搜索条件区域，放置搜索条件表单内容 |
| button | 按钮区域，放置查询/重置等操作按钮 |
