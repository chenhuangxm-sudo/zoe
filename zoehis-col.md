# zoehis-col 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-col 是一个列布局组件，必须作为 zoehis-row 的子组件使用。基于 24 栅格系统，支持 span（占据列数）、offset（偏移量）、order（排序）等属性，并会自动继承父级 zoehis-row 的 gutter、type、textAlign、labelAlign 等样式配置。

## 基础用法

```vue
<template>
  <zoehis-row :gutter="20">
    <zoehis-col :span="8" :offset="2">
      <zoehis-col-item label="字段1">内容1</zoehis-col-item>
    </zoehis-col>
    <zoehis-col :span="12">
      <zoehis-col-item label="字段2">内容2</zoehis-col-item>
    </zoehis-col>
  </zoehis-row>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| span | Number | 24 | 栅格占据的列数，基于 24 栅格系统 |
| order | Number / String | 0 | 排序，用于 Flex 布局的 order 属性 |
| offset | Number | 0 | 栅格左侧偏移的列数 |
| textAlign | String | '' | 文本对齐方式，会覆盖父级 row 的 textAlign |
| labelAlign | String | '' | 标签对齐方式，会覆盖父级 row 的 labelAlign |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，通常放置 zoehis-col-item 子组件 |
