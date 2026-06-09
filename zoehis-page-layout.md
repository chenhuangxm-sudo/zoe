# zoehis-page-layout 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-page-layout 是一个高级页面布局容器组件，内部集成了 zoehis-container、zoehis-header、zoehis-main、zoehis-footer、zoehis-aside 和 zoehis-partition 等组件，提供了一套完整的页面骨架布局方案。支持左侧边栏、右侧边栏、主区域分割、自定义各区域样式等功能。

## 基础用法

```vue
<template>
  <zoehis-page-layout
    :headerStyle="{ height: '60px' }"
    :leftAsideStyle="{ width: '200px' }"
    :mainStyle="{ background: '#f5f5f5' }"
    :footerStyle="{ height: '50px' }">
    <template slot="header">
      顶部导航
    </template>
    <template slot="left-aside">
      左侧菜单
    </template>
    <template slot="main">
      主体内容
    </template>
    <template slot="footer">
      底部信息
    </template>
  </zoehis-page-layout>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| leftAsidePartionFlag | Boolean | false | 左侧边栏是否启用分块分割（显示折叠按钮） |
| rightAsidePartionFlag | Boolean | false | 右侧边栏是否启用分块分割（显示折叠按钮） |
| mainPartionAttr | Object | {} | 主区域分割配置，支持 normalSize、activeSize、showArrow、draggable 等属性 |
| leftPartitionAttr | Object | {} | 左侧边栏分割配置，覆盖默认左侧分割属性 |
| rightPartitionAttr | Object | {} | 右侧边栏分割配置，覆盖默认右侧分割属性 |
| headerStyle | Object / String | {} | 头部区域自定义样式 |
| leftAsideStyle | Object / String | {} | 左侧边栏自定义样式 |
| rightAsideStyle | Object / String | {} | 右侧边栏自定义样式 |
| mainStyle | Object / String | {} | 主区域自定义样式 |
| footerStyle | Object / String | {} | 底部区域自定义样式 |
| topMainStyle | Object / String | { width: '100%', height: '100%' } | 主区域上半部分自定义样式（mainSplitFlag 为 true 时生效） |
| bottomMainStyle | Object / String | { width: '100%', height: '100%' } | 主区域下半部分自定义样式（mainSplitFlag 为 true 时生效） |
| singleLeftAsideFlag | Boolean | false | 左侧边栏是否为独立面板模式（不嵌套在 container 内） |
| singleRightAsideFlag | Boolean | false | 右侧边栏是否为独立面板模式（不嵌套在 container 内） |
| mainSplitFlag | Boolean | false | 主区域是否进行上下分割 |
| border | Boolean | true | 是否显示边框 |

### mainPartionAttr 默认值

```js
{
  normalSize: ['60%', '40%'],
  activeSize: ['calc(100% - 35px)', '35px'],
  showArrow: true,
  verticalArrow: ['z_dropU_form', 'z_dropD_form'],
  horizontalArrow: ['z_arrowTTL_normal', 'z_arrowTTR_normal'],
  lineDirection: false,
  draggable: false,
  minLeft: 30,
  minHeight: 35,
  iconCls: '',
  lineClass: ''
}
```

### 左侧边栏默认分割配置

```js
{
  normalSize: ['20%', '80%'],
  activeSize: ['0%', '100%'],
  showArrow: false,
  draggable: false,
  lineClass: 'zoehis_page_layout_line_style'
}
```

### 右侧边栏默认分割配置

```js
{
  normalSize: ['80%', '20%'],
  activeSize: ['calc(100% - 35px)', '35px'],
  showArrow: false,
  draggable: false,
  lineClass: 'zoehis_page_layout_line_style'
}
```

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| header | 头部区域内容 |
| main | 主区域内容（mainSplitFlag 为 false 时生效） |
| top-main | 主区域上半部分内容（mainSplitFlag 为 true 时生效） |
| bottom-main | 主区域下半部分内容（mainSplitFlag 为 true 时生效） |
| footer | 底部区域内容 |
| left-aside | 左侧边栏内容 |
| right-aside | 右侧边栏内容 |
