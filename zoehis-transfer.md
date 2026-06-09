# zoehis-transfer 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-transfer` 是一个穿梭框组件，支持左右两栏布局、搜索过滤、自定义标题、自定义左右区域内容、箭头按钮禁用控制等功能。

## 基础用法

```vue
<template>
  <zoehis-transfer
    searchflag
    left-title="待选项"
    right-title="已选项"
    @right-click="handleToRight"
    @left-click="handleToLeft"
    @search-input="handleSearch"
  >
    <template slot="leftMain">
      <!-- 左侧列表内容 -->
    </template>
    <template slot="rightMain">
      <!-- 右侧列表内容 -->
    </template>
  </zoehis-transfer>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| searchflag | Boolean | false | 是否显示搜索区 |
| searchParam | Object | {} | 搜索区配置，支持 `{ label, placeholder, width }` |
| delayTime | String/Number | — | 输入框延时时间 |
| leftTitle | String | — | 左侧标题 |
| rightTitle | String | — | 右侧标题 |
| uiType | String | — | UI 样式：`'rectangle'` 矩形输入框 |
| rightDisbaled | Boolean | false | 右箭头是否禁用 |
| leftDisbaled | Boolean | false | 左箭头是否禁用 |
| leftWidth | String | — | 左侧宽度 |
| rightWidth | String | — | 右侧宽度 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| search-input | (val) | 搜索区输入时触发 |
| search-change | (val) | 搜索区值改变时触发 |
| search-clickicon | (val, e) | 搜索区图标点击时触发 |
| right-click | (e) | 右箭头点击时触发 |
| left-click | (e) | 左箭头点击时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| transferSearch | 自定义搜索区域 |
| leftTitle | 自定义左侧标题 |
| leftMain | 左侧主体内容 |
| rightTitle | 自定义右侧标题 |
| rightMain | 右侧主体内容 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| setSearchValue | (val) | 设置搜索区的值 |
| searchFocus | — | 使搜索区输入框获取焦点 |
