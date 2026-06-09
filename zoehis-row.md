# zoehis-row 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-row 是一个行布局容器组件，基于 Flex 布局实现，用于配合 zoehis-col 和 zoehis-col-item 构建栅格布局系统。支持 gutter（栅格间距）、标签对齐方式、标签后缀、文本对齐等属性，并支持 search 和 single/multiple 等类型样式。

## 基础用法

```vue
<template>
  <zoehis-row :gutter="20" type="single" labelWidth="100px">
    <zoehis-col :span="12">
      <zoehis-col-item label="姓名">张三</zoehis-col-item>
    </zoehis-col>
    <zoehis-col :span="12">
      <zoehis-col-item label="年龄">25</zoehis-col-item>
    </zoehis-col>
  </zoehis-row>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| gutter | Number | 0 | 栅格间隔，单位为 px |
| gutterSide | Boolean | false | 是否保留两边的间隔，true 表示两边间隔保留 |
| type | String | '' | 类型，可选值：`single` / `multiple` / `search` |
| labelSuffix | String | '：' | 标签文本后缀 |
| labelWidth | String | '' | 标签宽度，如 `100px` |
| justify | String | '' | Flex 主轴对齐方式，对应 `justify-content` 属性 |
| textAlign | String | '' | 文本对齐方式 |
| labelAlign | String | '' | 标签对齐方式 |
| group | Boolean | false | 检索时分组会用到，添加分组样式 |
| labelStyle | Object | {} | 自定义标签样式 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置 zoehis-col 或 zoehis-col-item 子组件 |
