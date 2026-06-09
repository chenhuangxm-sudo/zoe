# zoehis-scrollbar 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

自定义滚动条组件，支持原生滚动条和虚拟滚动条两种模式。可自定义滚动条尺寸、样式，支持滚动事件监听、滚动位置控制等功能，用于美化或统一浏览器滚动条样式。

## 基础用法

```vue
<zoehis-scrollbar
  :native="false"
  :noresize="false"
  size="default"
  style="height: 300px;"
>
  <div style="height: 600px;">
    <!-- 滚动内容 -->
  </div>
</zoehis-scrollbar>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| native | Boolean | false | 是否使用原生滚动条 |
| wrapStyle | - | - | 父容器样式（对象、数组或字符串） |
| nativeWrapStyle | Object | {} | 原生模式下的父容器样式 |
| wrapClass | - | - | 父容器 class |
| viewStyle | - | - | 滚动区域样式 |
| viewClass | - | - | 滚动区域 class |
| noresize | Boolean | - | 如果容器尺寸不会发生变化，设置 true 可优化性能 |
| delayTime | Number | 30 | 滚动事件触发延迟（毫秒） |
| tag | String | 'div' | 滚动区域生成的元素标签名 |
| verticalbar | Boolean | false | 是否一直显示竖向滚动条（native=true 时有效） |
| size | String | 'default' | 滚动条尺寸（default / small） |
| width | Number/String | '' | 滚动条宽度 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| scrollafter | (wrap) | 滚动后触发，返回滚动容器对象 |
| scrollresize | (wrap) | 滚动条重新设置时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| move | (axis) | 设置滚动条滚动位置，axis 为 `{top: Number, left: Number}` |
| update | - | 更新滚动条大小 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 滚动区域内容 |
