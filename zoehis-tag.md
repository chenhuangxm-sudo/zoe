# zoehis-tag 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-tag` 是一个标签组件，支持多种类型（朴素、圆角、表单）、自定义颜色/背景、可关闭、与 `zoehis-tag-group` 配合使用等功能。

## 基础用法

```vue
<template>
  <div>
    <zoehis-tag type="plain">默认标签</zoehis-tag>
    <zoehis-tag type="fillet" closable>可关闭标签</zoehis-tag>
    <zoehis-tag
      type="form"
      color="#409EFF"
      background-color="#ecf5ff"
    >自定义颜色</zoehis-tag>
  </div>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| type | String | 'plain' | 标签类型：`plain`（朴素）、`fillet`（圆角）、`form`（表单） |
| theme | String | 'default' | 样式主题：`default`、`other` |
| customClass | String | '' | 自定义类名 |
| color | String | '' | 自定义字体颜色 |
| backgroundColor | String | '' | 自定义背景颜色 |
| closable | Boolean | false | 是否可关闭 |
| data | Object | — | 标签关联数据 |
| title | String/Number | '' | 标签显示文本 |
| code | String/Number | '' | 标签标识 code |
| tagCode | String | 'code' | 数据中 code 字段名 |
| tagTitle | String | 'title' | 数据中 title 字段名 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| click | (e) | 标签点击时触发（原生 click 事件） |

> 注：与 `zoehis-tag-group` 配合使用时，`tag-group` 会处理 `tag-click` 和 `tag-close` 事件。

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 标签内容，未提供时显示 `title` 或 `data[tagTitle]` |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| remove | — | 从 tag-group 中移除自身 |
