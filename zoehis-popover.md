# zoehis-popover 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

弹出框组件，支持 hover/click/manual 三种触发方式，可设置弹出位置（上/下/左/右）、偏移量、嵌套模式、手动控制显示隐藏等。适用于工具提示、下拉菜单、弹出面板等场景。

## 基础用法

```vue
<zoehis-popover
  placement="right"
  trigger="hover"
  width="200"
>
  <template slot="reference">
    <button>鼠标悬停</button>
  </template>
  <div>弹出内容</div>
</zoehis-popover>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| visibleFlag | Boolean | false | 手动模式下的显示状态 |
| width | Number/String | '' | 弹出框宽度 |
| height | Number/String | '' | 弹出框高度 |
| trigger | String | 'hover' | 触发方式：hover / click / manual |
| placement | String | 'right' | 弹出位置：right / left / bottom / top |
| offsetX | Number/String | '' | 水平方向偏移量 |
| offsetY | Number/String | '' | 垂直方向偏移量 |
| disabled | Boolean | false | 是否禁用弹出 |
| nestedFlag | Boolean | false | 是否嵌套模式（嵌套时鼠标移入移出不自动隐藏） |
| hidePop | Boolean | false | 是否隐藏 popover（nestedFlag=true 时生效） |
| preventOverId | String | '' | 弹出框容器的 ID |
| appendToBody | Boolean | true | 是否将弹出框插入到 body |
| isNesting | Boolean | false | 是否嵌套使用（级联组件内部使用） |
| isShowPattern | Boolean | false | 是否使用 v-show 控制显示 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| show | - | 弹出框显示时触发 |
| hide | - | 弹出框隐藏时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| show | - | 显示弹出框 |
| hide | - | 隐藏弹出框 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| reference | 触发弹出框的元素 |
| default | 弹出框内容 |
