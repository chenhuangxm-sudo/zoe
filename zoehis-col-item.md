# zoehis-col-item 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-col-item 是一个表单项展示组件，通常作为 zoehis-col 的子组件使用。它由标签区域（label）和内容区域两部分组成，支持标签宽度、必填标记、自定义标签样式等功能。当设置 `line` 属性为 true 时，可渲染为横线分隔样式。

## 基础用法

```vue
<template>
  <zoehis-row labelWidth="100px">
    <zoehis-col :span="12">
      <zoehis-col-item label="姓名" required>张三</zoehis-col-item>
    </zoehis-col>
    <zoehis-col :span="12">
      <zoehis-col-item label="年龄">25</zoehis-col-item>
    </zoehis-col>
    <zoehis-col :span="24">
      <zoehis-col-item line></zoehis-col-item>
    </zoehis-col>
  </zoehis-row>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| label | String | '' | 标签文本内容 |
| labelSuffix | String | '' | 标签后缀，优先级高于父级 row 的 labelSuffix |
| labelWidth | String | '' | 标签宽度，优先级高于父级 row 的 labelWidth |
| required | Boolean | false | 是否必填，为 true 时标签前显示红色必填标记 |
| line | Boolean | false | 是否渲染为横线分隔样式 |
| labelWidthFixed | Boolean | false | 是否强制固定标签宽度（内部使用） |
| labelStyle | Object | {} | 自定义标签样式，会与父级 row 的 labelStyle 合并 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置内容区域 |
