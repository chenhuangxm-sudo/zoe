# zoehis-empty 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-empty` 是一个空状态占位组件，支持多种内置 SVG 图片、自定义图片、自定义描述文字、三种布局模式（垂直、水平、纯文本），可根据容器尺寸自动切换布局。

## 基础用法

```vue
<template>
  <zoehis-empty description="暂无数据"></zoehis-empty>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| image | Component/String | defaultEmpty | 内置图片类型，可选内置组件：`defaultEmpty`、`appendEmpty`、`dataEmpty`、`distributeEmpty`、`documentEmpty`、`messageEmpty` |
| imageHeight | String | '' | 图片高度，支持数字（自动加 px）或带单位的字符串 |
| imageWidth | String | '' | 图片宽度，支持数字（自动加 px）或带单位的字符串 |
| description | String | '暂无数据' | 描述文字 |
| uiType | String | '' | 布局类型：`'vertical'`（垂直）、`'horizontal'`（水平）、`'text'`（纯文本）。不设置时根据容器尺寸自动切换 |

## 事件（Events）

无事件。

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| image | 自定义图片区域 |
| description | 自定义描述区域 |
| default | 底部追加内容，通常放置操作按钮 |
