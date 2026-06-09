# zoehis-dialog 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-dialog` 是一个功能丰富的弹窗对话框组件，支持拖拽移动、缩放大小、遮罩层、错误详情展开/收起、快捷键关闭、新版模式（高度自适应）等特性。

## 基础用法

```vue
<template>
  <zoehis-dialog
    :visible.sync="dialogVisible"
    title="提示"
    :width="500"
    :height="300"
    @open="handleOpen"
    @close="handleClose"
  >
    <p>弹窗内容</p>
    <template slot="footer">
      <zoehis-button @clickenter="dialogVisible = false">取消</zoehis-button>
      <zoehis-button type="primary" @clickenter="handleConfirm">确认</zoehis-button>
    </template>
  </zoehis-dialog>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| visible | Boolean | — | 是否显示弹窗，支持 `.sync` 修饰符 |
| title | String | "提示" | 弹窗标题，设为空字符串则不显示标题栏 |
| modal | Boolean | true | 是否显示黑色遮罩 |
| modalAppendToBody | Boolean | false | 黑色遮罩是否插入到 body 下 |
| width | Number/String | 420 | 弹窗宽度，支持数字（px）或百分比字符串 |
| height | Number/String | 235 | 弹窗高度，支持数字（px）或百分比字符串 |
| closeOnClickModal | Boolean | false | 点击遮罩是否关闭弹窗 |
| closeOnPressEscape | Boolean | true | 按 ESC 键是否关闭弹窗 |
| beforeClose | Function | — | 关闭前回调函数，接收 `hide` 方法和关闭标识作为参数 |
| errorSlideDownName | String | "收起详情信息" | 错误详情展开时的收起按钮文本 |
| errorSlideUpName | String | "展开详情信息" | 错误详情收起时的展开按钮文本 |
| headerclose | Boolean | false | 是否显示标题栏关闭图标 |
| supportdrag | Boolean | true | 是否支持拖拽移动 |
| newscrollbar | Boolean | false | 是否启用新版滚动条优化 |
| bodyscroll | Boolean | false | 内容部分是否需要滚动条 |
| appendToBody | Boolean | false | 是否将弹窗 DOM 插入到 body 下 |
| positionStyle | Object | {} | 初始化时的位置，如 `{ top: '100px', left: '200px' }` |
| alwaysInitPosition | Boolean | false | 每次打开弹窗是否重新初始化位置 |
| mode | String | — | 模式，设为 `'new'` 时启用新版弹窗，支持高度自适应 |
| native | Boolean | false | 是否使用原生滚动条 |
| resizable | Boolean | — | 是否支持缩放（来自 dialogMixin） |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| open | — | 弹窗打开时触发 |
| close | — | 弹窗关闭时触发 |
| headerclose | — | 点击标题栏关闭图标时触发 |
| update:visible | Boolean | 弹窗显示状态变化时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 弹窗主体内容 |
| footer | 弹窗底部操作区 |
| error | 错误详情区域 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| scrollMove | (left, top) | 滚动条移动到指定位置 |
| show | — | 显示弹窗 |
| hide | (cancel) | 隐藏弹窗，传入 `false` 阻止隐藏 |
| toggleErrorDetail | (val) | 切换错误详情展开/收起状态 |
| winDispatchEvent | (name) | 主动触发 window 自定义事件 |
