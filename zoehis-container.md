# zoehis-container / zoehis-header / zoehis-main / zoehis-footer / zoehis-aside 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

这是一组页面布局容器组件，用于构建页面的整体骨架布局：

- **zoehis-container**：外层容器，自动检测子组件方向，支持水平/垂直布局
- **zoehis-header**：顶部区域容器，支持可拖拽分割功能
- **zoehis-main**：主体内容区域容器，支持可拖拽分割功能，可配置分割方向
- **zoehis-footer**：底部区域容器，支持可拖拽分割功能
- **zoehis-aside**：侧边栏容器，支持可拖拽分割功能，可配置左右位置

所有带分割功能的组件（header/main/footer/aside）均通过 `partitionMixin` 混入实现统一的拖拽分割逻辑。

## 基础用法

```vue
<template>
  <zoehis-container direction="vertical">
    <zoehis-header height="60px">
      顶部区域
    </zoehis-header>
    <zoehis-container>
      <zoehis-aside width="200px" direction="left">
        左侧边栏
      </zoehis-aside>
      <zoehis-main>
        主体内容
      </zoehis-main>
    </zoehis-container>
    <zoehis-footer height="50px">
      底部区域
    </zoehis-footer>
  </zoehis-container>
</template>
```

---

## zoehis-container

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| direction | String | - | 布局方向，可选值：`vertical`（垂直）、`horizontal`（水平）。不传时自动检测：包含 zoehis-header 或 zoehis-footer 时为垂直布局 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置 header / main / footer / aside 子组件 |

---

## zoehis-header

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| height | String | '40px' | 头部高度 |
| direction | String | 'bottom' | 分割线位置，仅支持 `bottom` |
| isPartition | Boolean | false | 是否启用分割功能 |
| showArrow | Boolean | true | 是否显示折叠按钮 |
| uiType | String | 'default' | 组件 UI 类型 |
| partitionIcons | Array | ['z_dropU_form', 'z_dropD_form'] | 分割按钮图标 |
| draggable | Boolean | false | 是否可拖拽 |
| activeSize | String | '25px' | 激活状态（折叠后）的尺寸 |
| minLeft | Number | 35 | 最小上/左侧限制范围 |
| minRight | Number | 35 | 最小下/右侧限制范围 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| iconClick | (iconStatus: Number) | 按钮图标点击事件，0：默认状态，1：点击状态 |
| drag | (finalSize: String) | 拖拽过程中触发，返回最终尺寸 |
| dragmove | (moveLen: Number) | 拖拽移动事件，返回移动距离 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置头部内容 |

---

## zoehis-main

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| direction | String | 'bottom' | 分割线位置，支持 `left` / `right` / `top` / `bottom` |
| isPartition | Boolean | false | 是否启用分割功能 |
| showArrow | Boolean | true | 是否显示折叠按钮 |
| uiType | String | 'default' | 组件 UI 类型 |
| partitionIcons | Array | - | 自定义分割按钮图标，不传时根据 direction 自动匹配 |
| draggable | Boolean | false | 是否可拖拽 |
| activeSize | String | '25px' | 激活状态（折叠后）的尺寸 |
| minLeft | Number | 35 | 最小上/左侧限制范围 |
| minRight | Number | 35 | 最小下/右侧限制范围 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| iconClick | (iconStatus: Number) | 按钮图标点击事件，0：默认状态，1：点击状态 |
| drag | (finalSize: String) | 拖拽过程中触发，返回最终尺寸 |
| dragmove | (moveLen: Number) | 拖拽移动事件，返回移动距离 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置主体内容 |

---

## zoehis-footer

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| height | String | '50px' | 底部高度 |
| direction | String | 'top' | 分割线位置，仅支持 `top` |
| isPartition | Boolean | false | 是否启用分割功能 |
| showArrow | Boolean | true | 是否显示折叠按钮 |
| uiType | String | 'default' | 组件 UI 类型 |
| partitionIcons | Array | ['z_dropD_form', 'z_dropU_form'] | 分割按钮图标 |
| draggable | Boolean | false | 是否可拖拽 |
| activeSize | String | '25px' | 激活状态（折叠后）的尺寸 |
| minLeft | Number | 35 | 最小上/左侧限制范围 |
| minRight | Number | 35 | 最小下/右侧限制范围 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| iconClick | (iconStatus: Number) | 按钮图标点击事件，0：默认状态，1：点击状态 |
| drag | (finalSize: String) | 拖拽过程中触发，返回最终尺寸 |
| dragmove | (moveLen: Number) | 拖拽移动事件，返回移动距离 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置底部内容 |

---

## zoehis-aside

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| width | String | '200px' | 侧边栏宽度 |
| direction | String | 'right' | 分割线位置，支持 `left` / `right` |
| isPartition | Boolean | false | 是否启用分割功能 |
| showArrow | Boolean | true | 是否显示折叠按钮 |
| uiType | String | 'default' | 组件 UI 类型 |
| partitionIcons | Array | - | 自定义分割按钮图标，不传时根据 direction 自动匹配 |
| draggable | Boolean | false | 是否可拖拽 |
| activeSize | String | '25px' | 激活状态（折叠后）的尺寸 |
| minLeft | Number | 35 | 最小上/左侧限制范围 |
| minRight | Number | 35 | 最小下/右侧限制范围 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| iconClick | (iconStatus: Number) | 按钮图标点击事件，0：默认状态，1：点击状态 |
| drag | (finalSize: String) | 拖拽过程中触发，返回最终尺寸 |
| dragmove | (moveLen: Number) | 拖拽移动事件，返回移动距离 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置侧边栏内容 |
