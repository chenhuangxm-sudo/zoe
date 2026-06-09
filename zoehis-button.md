# zoehis-button 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-button` 是一个功能丰富的按钮组件，支持多种类型（默认、主要、功能键、删除等）、多种尺寸（正常、小型、大型），以及图标、快捷键、禁用、圆形图标等特性。配合 `zoehis-button-group` 按钮组组件可实现按钮分组、超出折叠等功能。

## 基础用法

```vue
<!-- 基础按钮 -->
<zoehis-button type="primary" @clickenter="handleClick">主要按钮</zoehis-button>
<zoehis-button type="default">默认按钮</zoehis-button>
<zoehis-button type="delete">删除按钮</zoehis-button>

<!-- 不同尺寸 -->
<zoehis-button size="small">小型按钮</zoehis-button>
<zoehis-button size="normal">正常按钮</zoehis-button>
<zoehis-button size="big">大型按钮</zoehis-button>

<!-- 带图标 -->
<zoehis-button icon="z_add_normal" type="features">新增</zoehis-button>

<!-- 禁用状态 -->
<zoehis-button :disabled="true">禁用按钮</zoehis-button>

<!-- 圆形图标按钮 -->
<zoehis-button circle icon="z_search_normal"></zoehis-button>

<!-- 按钮组 -->
<zoehis-button-group>
  <zoehis-button type="primary">保存</zoehis-button>
  <zoehis-button>取消</zoehis-button>
</zoehis-button-group>
```

## 属性（Props）

### ZoehisButton

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| type | String | 'default' | 按钮类型：default（默认）、primary（主要的）、features（底部按钮功能键）、plain（无图标圆角略小按钮）、plainPrimary（无图标圆角略小主要按钮）、delete（删除按钮）、clearCard（清卡按钮） |
| size | String | 'normal' | 按钮尺寸：normal（正常）、small（小型）、big（大型） |
| icon | String | — | 图标类名，目前主要针对底部按钮图标 |
| keyboard | String / Number | — | 按钮快捷键标识数字 |
| disabled | Boolean | false | 是否禁用 |
| shrinkLevel | Number / String | 1 | 收缩等级，值越高越先被收起来 |
| width | Number / String | '' | 按钮宽度 |
| label | Number / String | '' | 按钮标签值，用于按钮组判断激活状态 |
| circle | Boolean | false | 是否为圆形图标按钮 |
| sortNo | Number | — | 排序号 |

### ZoehisButtonGroup

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| activedLabel | Number / String | '' | 当前激活的按钮 label 值 |
| type | String | '' | 按钮组类型，vertical 方向下默认为 cardComplex |
| direction | String | 'horizontal' | 按钮组排列方向：horizontal（横向）、vertical（竖向） |
| overType | String | 'dots' | 超出时显示的按钮样式：dots（省略号）、more（更多） |
| sonButtonName | String | 'ZoehisButton' | 内部使用，子按钮组件名称 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| clickenter | (evt) | 按钮点击或回车触发 |
| focus | (evt) | 按钮获取焦点时触发 |
| blur | (evt) | 按钮失去焦点时触发 |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| focus | — | 手动聚焦到按钮 |
| blur | — | 手动使按钮失去焦点 |
| getDisabled | — | 获取按钮是否禁用，返回 Boolean |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 按钮文本内容 |
