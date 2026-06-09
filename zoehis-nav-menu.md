# zoehis-nav-menu 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

导航菜单组件，支持垂直布局、折叠/展开、折叠动画、双色图标等功能。配合 `zoehis-menu-item` 和 `zoehis-submenu` 子组件使用，适用于侧边栏导航菜单场景。

## 基础用法

```vue
<zoehis-nav-menu
  defaultActive="1"
  :collapse="false"
  :collapsible="true"
  @change="handleChange"
  @select="handleSelect"
>
  <zoehis-menu-item index="1" icon="z_setup_normal">菜单一</zoehis-menu-item>
  <zoehis-submenu index="2" icon="z_setup_normal">
    <template slot="title">菜单二</template>
    <zoehis-menu-item index="2-1">子菜单项一</zoehis-menu-item>
    <zoehis-menu-item index="2-2">子菜单项二</zoehis-menu-item>
  </zoehis-submenu>
  <zoehis-menu-item index="3" icon="z_setup_normal">菜单三</zoehis-menu-item>
</zoehis-nav-menu>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| defaultActive | String | '' | 当前激活菜单的 index |
| collapse | Boolean | false | 是否水平折叠收起菜单 |
| collapseTransition | Boolean | true | 是否开启折叠动画 |
| collapsible | Boolean | true | 是否启用菜单收缩功能 |
| multicolor | Boolean | false | 是否启用双色（SVG）图标 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| change | (val, title) | 菜单选中项发生变化时触发 |
| collapseChange | (collapseFlag) | 折叠状态变化时触发 |
| select | (index, keyPath, title) | 菜单项被选中时触发 |
| open | (index, keyPath) | 子菜单展开时触发 |
| close | (index, keyPath) | 子菜单收起时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 菜单项列表（zoehis-menu-item / zoehis-submenu） |
