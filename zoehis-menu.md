# zoehis-menu / zoehis-menu-group / zoehis-menu-item / zoehis-submenu 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

菜单组件系列，包含 `zoehis-menu-group`（菜单组容器）、`zoehis-menu`（菜单项）、`zoehis-menu-item`（导航菜单项）和 `zoehis-submenu`（导航子菜单）四个组件。支持多种风格样式（style1~style6）、菜单收缩、右键菜单、Badge 徽标、关闭图标等功能，适用于标签页导航、侧边栏导航等场景。

---

## zoehis-menu-group 菜单组

### 基础用法

```vue
<zoehis-menu-group
  v-model="activeMenu"
  type="style1"
  :menuList="menuList"
  itemcode="code"
  itemtext="text"
>
  <zoehis-menu
    v-for="item in menuList"
    :key="item.code"
    :label="item.code"
    :text="item.text"
  >
    {{ item.text }}
  </zoehis-menu>
</zoehis-menu-group>
```

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| value | - | - | 当前选中的值，支持 v-model |
| activeName | - | - | 激活项名称 |
| type | String | 'style1' | 菜单风格类型：style1 / style2 / style3 / style4 / style5 |
| disabled | Boolean | false | 是否禁用 |
| hover | Boolean | false | 是否启用 hover 效果 |
| closeable | Boolean | false | 是否显示关闭按钮 |
| badgeFlag | Boolean | - | 是否显示 Badge |
| badgeType | String | '' | Badge 类型 |
| badgeMax | String/Number | - | Badge 最大值 |
| beforeClick | Function | - | 点击前回调函数 |
| menuList | Array | [] | 菜单列表数据 |
| itemtext | String | 'itemtext' | 菜单项显示文本的字段名 |
| itemcode | String | 'itemcode' | 菜单项标识的字段名 |
| iconClass | String | 'z_close_normal02' | 关闭图标类名 |
| collapsible | Boolean | false | 是否启用菜单收缩功能（超出后显示"更多"下拉） |
| rightClick | Boolean | false | 是否开启右键菜单 |
| rightClickData | Array | [{code:'close',title:'关闭'},{code:'closeOther',title:'关闭其它'},{code:'closeAll',title:'关闭全部'}] | 右键菜单数据 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| change | (value, oldValue) | 选中值发生变化时触发 |
| closeIconClick | (label) | 点击关闭图标时触发 |
| rightClickEn | (type, label) | 右键菜单选择后触发 |

### 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| init | - | 重新矫正菜单组的收缩功能（当菜单组宽度变化后调用） |

---

## zoehis-menu 菜单项

### 基础用法

```vue
<zoehis-menu
  label="menu1"
  text="菜单一"
  :disabled="false"
  badgeValue="3"
  badgeType="primary"
>
  菜单一
</zoehis-menu>
```

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| label | - | - | 菜单项标识值 |
| text | - | - | 菜单项显示文本 |
| disabled | Boolean | false | 是否禁用 |
| badgeFlag | Boolean | - | 是否显示 Badge |
| badgeType | String | - | Badge 类型 |
| badgeValue | String/Number | '' | Badge 显示值 |
| badgeMax | String/Number | - | Badge 最大值 |
| closeable | Boolean | false | 是否显示关闭图标 |
| iconClass | String | - | 关闭图标类名 |
| uiType | String | - | UI 类型（用于区分新旧代码，如 'oneLink'） |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| menuClick | (label, oldLabel) | 菜单项被点击时触发 |
| closeIconClick | (label) | 点击关闭图标时触发 |
| rightClickEn | (type, label) | 右键菜单选择后触发 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 菜单项显示内容 |

---

## zoehis-menu-item 导航菜单项

> 属于 `zoehis-nav-menu` 子组件

### 基础用法

```vue
<zoehis-menu-item index="1" icon="z_setup_normal">
  菜单项一
</zoehis-menu-item>
```

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| index | String | '' | 菜单项的唯一标识 |
| icon | String | '' | 图标类名 |
| paddingLeft | Number/String | '' | 自定义左内边距 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| (通过 navMenu 触发) select | (index, keyPath, title) | 菜单项被选中时触发 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 菜单项默认内容 |
| title | 菜单项标题内容 |

---

## zoehis-submenu 导航子菜单

> 属于 `zoehis-nav-menu` 子组件

### 基础用法

```vue
<zoehis-submenu index="1-1" icon="z_setup_normal">
  <template slot="title">子菜单标题</template>
  <zoehis-menu-item index="1-1-1">选项一</zoehis-menu-item>
  <zoehis-menu-item index="1-1-2">选项二</zoehis-menu-item>
</zoehis-submenu>
```

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| index | String | '' | 子菜单的唯一标识 |
| icon | String | '' | 图标类名 |
| paddingLeft | Number/String | '' | 自定义左内边距 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| title | 子菜单标题内容 |
| default | 子菜单项列表内容 |
