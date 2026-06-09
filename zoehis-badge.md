# zoehis-badge 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

徽标/角标组件，用于在图标或文字右上角显示消息数量、红点等提示信息。支持设置最大值（超出显示 N+）、多种颜色类型、隐藏控制等。

## 基础用法

```vue
<zoehis-badge :value="12" :max="99" type="primary">
  <span>消息中心</span>
</zoehis-badge>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | String/Number | '' | 显示值 |
| type | String | 'primary' | 类型：primary / info / warning |
| hidden | Boolean | - | 是否隐藏 badge |
| max | String/Number | '' | 最大值，超过最大值会显示 '{max}+' |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 被徽标包裹的元素 |
