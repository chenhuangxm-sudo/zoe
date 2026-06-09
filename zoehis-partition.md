# zoehis-partition 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

zoehis-partition 是一个可拖拽分割面板组件，将容器分为左右（或上下）两个区域，支持拖拽调整区域大小、折叠/展开切换、自定义尺寸和图标等功能。可用于页面布局中的区域分割场景。

## 基础用法

```vue
<template>
  <zoehis-partition
    mode="horizontal"
    :normalSize="['70%', '30%']"
    :activeSize="['calc(100% - 35px)', '35px']"
    :draggable="true"
    :showArrow="true"
    v-model="isCollapsed">
    <template slot="left">
      <div>左侧区域内容</div>
    </template>
    <template slot="right">
      <div>右侧区域内容</div>
    </template>
  </zoehis-partition>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| normalSize | Array | ['50%', '50%'] | 默认状态下的左右/上下区域尺寸比例 |
| activeSize | Array | ['calc(100% - 35px)', '35px'] | 折叠状态下的左右/上下区域尺寸 |
| verticalArrow | Array | ['z_dropU_form', 'z_dropD_form'] | 垂直布局时的图标数组，[展开图标, 折叠图标] |
| horizontalArrow | Array | ['z_arrowTTL_normal', 'z_arrowTTR_normal'] | 水平布局时的图标数组，[展开图标, 折叠图标] |
| mode | String | 'vertical' | 布局方向，可选值：`vertical`（垂直/上下）、`horizontal`（水平/左右） |
| showArrow | Boolean | true | 是否显示折叠/展开按钮 |
| value / v-model | Boolean | false | 折叠/展开状态，true 为折叠状态 |
| lineDirection | Boolean | false | 分割线样式区别，默认 false |
| draggable | Boolean | false | 是否支持拖拽调整大小 |
| minLeft | Number | 30 | 最小允许向左/向上拖动的距离（边界限制） |
| minRight | Number | 35 | 最小允许向右/向下拖动的距离（边界限制） |
| iconCls | String | '' | 自定义按钮的 class 名称 |
| lineClass | String | '' | 自定义分割线的 class 名称 |
| uiType | String | 'default' | UI 类型，设为 `sample` 时启用简约样式 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| input | (value: Boolean) | v-model 双向绑定事件，折叠状态变化时触发 |
| dragstop | (curSize: Array) | 拖拽停止时触发，返回当前左右区域尺寸数组 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| left | 左侧（或上方）区域内容 |
| right | 右侧（或下方）区域内容 |
