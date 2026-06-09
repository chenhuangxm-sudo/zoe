# zoehis-progress-popup 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-progress-popup` 是一个进度弹窗组件，用于展示批量处理任务的执行进度，支持进度条显示、成功/失败统计、刷新重试、错误详情查看、多种 UI 主题（含简易黑色模式）等功能。

## 基础用法

```vue
<template>
  <zoehis-progress-popup
    :visible.sync="progressVisible"
    :total="100"
    :done-value="doneValue"
    :error-value="errorValue"
    closeable
    @close="handleClose"
    @refresh="handleRefresh"
  ></zoehis-progress-popup>
</template>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| visible | Boolean | false | 是否显示弹窗，支持 `.sync` 修饰符 |
| total | Number | 100 | 任务总数 |
| doneValue | Number | 0 | 已处理完成的数量 |
| errorValue | Number | 0 | 处理失败的数量 |
| loading | Boolean | false | 是否显示加载中状态 |
| decimal | Boolean | false | 百分比是否保留一位小数 |
| closeable | Boolean | false | 完成时是否显示右上角关闭按钮 |
| mask | Boolean | true | 是否显示遮罩层 |
| color | String | — | 进度条颜色 |
| refreshBt | Boolean | false | 是否显示刷新按钮 |
| doneState | String | — | 完成时的文本描述 |
| doingState | String | — | 正在执行时的文本描述 |
| waitState | String | — | 还没开始时的文本描述 |
| uiType | String | '' | UI 主题：`'simpleBlack'` 简易黑色主题 |
| zindex | String | — | 自定义 z-index |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| close | — | 点击关闭按钮时触发 |
| refresh | — | 点击刷新按钮时触发 |
| error-link | — | 点击"点击查看"错误链接时触发 |
| update:visible | Boolean | 弹窗显示状态变化时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| tip | 提示区域，位于状态文本旁 |
| doingDesc | 执行中的描述区域，默认显示"总共 N 人，当前第 M 人" |
| doneDesc | 执行完成的描述区域，默认显示完成统计或失败信息 |
