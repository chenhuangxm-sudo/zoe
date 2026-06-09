# zoehis-drawer 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-drawer` 是一个抽屉组件，支持从四个方向（左、右、上、下）滑出，可配置遮罩层、关闭按钮、尺寸调整等功能。

## 基础用法

```vue
<template>
  <zoehis-drawer
    :visible.sync="drawerVisible"
    title="抽屉标题"
    direction="rtl"
    :size="'300px'"
    @open="handleOpen"
    @close="handleClose"
  >
    <p>抽屉内容</p>
  </zoehis-drawer>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| visible | Boolean | — | 是否显示抽屉，支持 `.sync` 修饰符 |
| title | String | '' | 抽屉标题 |
| direction | String | 'rtl' | 抽屉弹出方向：`ltr`（从左向右）、`rtl`（从右向左）、`ttb`（从上向下）、`btt`（从下向上） |
| size | String | '260px' | 抽屉宽度（水平方向）或高度（垂直方向） |
| beforeClose | Function | — | 关闭前回调函数，接收 `hide` 方法作为参数 |
| showClose | Boolean | true | 是否显示关闭按钮 |
| withHeader | Boolean | true | 是否显示头部 |
| modal | Boolean | true | 是否显示遮罩层 |
| mask | Boolean | true | 是否挡住后面的内容（false 时遮罩透明） |
| wrapperClosable | Boolean | false | 点击遮罩是否关闭抽屉 |
| closeOnPressEscape | Boolean | false | 按 ESC 键是否关闭抽屉 |
| destroyOnClose | Boolean | false | 关闭时是否销毁子元素 |
| appendToBody | Boolean | true | 是否将抽屉 DOM 插入到 body 下 |
| modalAppendToBody | Boolean | true | 遮罩层是否插入到 body 下 |
| customClass | String | '' | 自定义类名 |
| wraperStl | Object | — | 覆盖 wrapper 的样式 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| open | — | 抽屉打开时触发 |
| opened | — | 抽屉打开动画完成后触发 |
| close | — | 抽屉关闭时触发 |
| closed | — | 抽屉关闭动画完成后触发 |
| update:visible | Boolean | 抽屉显示状态变化时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 抽屉主体内容 |
| title | 自定义标题区域（替换默认标题） |
