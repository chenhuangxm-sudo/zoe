# zoehis-tree 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

`zoehis-tree` 是一个树形控件组件，支持复选框、节点懒加载、拖拽排序、节点过滤、自定义节点内容、展开/折叠、节点增删改等丰富功能。

## 基础用法

```vue
<template>
  <zoehis-tree
    :data="treeData"
    :props="defaultProps"
    show-checkbox
    @node-click="handleNodeClick"
    @check-change="handleCheckChange"
  ></zoehis-tree>
</template>

<script>
export default {
  data() {
    return {
      treeData: [
        { id: 1, label: '一级 1', children: [{ id: 11, label: '二级 1-1' }] },
        { id: 2, label: '一级 2' }
      ],
      defaultProps: {
        children: 'children',
        label: 'label',
        id: 'id',
        pid: 'pid'
      }
    }
  }
}
</script>
```

## 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| data | Array | — | 树数据（扁平或树形结构） |
| props | Object | — | 配置选项：`{ children, label, id, pid, noleaf }` |
| propMap | Object | — | 替代 props 的配置映射 |
| lazy | Boolean | false | 是否懒加载子节点 |
| load | Function | — | 加载子树数据的方法 |
| showcheckbox | Boolean | false | 是否显示复选框 |
| showhalfcheckbox | Boolean | false | 是否显示半选状态样式 |
| checkstrictly | Boolean | false | 是否严格遵循父子不互相关联 |
| highlightcurrent | Boolean | true | 是否高亮当前选中节点 |
| defaultcheckedkeys | Array | — | 默认勾选的节点 key 数组 |
| defaultexpandedkeys | Array | — | 默认展开的节点 key 数组 |
| defaultexpandall | Boolean | false | 是否默认展开所有节点 |
| autoexpandparent | Boolean | true | 展开子节点时是否自动展开父节点 |
| expandonclicknode | Boolean | false | 点击节点时是否展开/折叠 |
| checkedclicknode | Boolean | false | 点击节点时是否切换选中 |
| currentnodekey | String/Number | — | 当前选中节点的 key |
| expandselected | Boolean | false | 选中节点时是否展开 |
| expandselectedchild | Boolean | true | 选中节点时是否展开子节点 |
| emptytext | String | '暂无数据' | 空数据时显示的文本 |
| filterNodeMethod | Function | — | 节点过滤方法 |
| beforenodeselect | Function | — | 节点选择前的回调 |
| draggable | Boolean | false | 是否允许拖拽 |
| allowDrag | Function | — | 判断节点能否被拖拽 |
| allowDrop | Function | — | 判断节点能否被拖入目标 |
| editable | Boolean | false | 是否允许双击编辑 |
| renderhtml | Function | — | 自定义节点渲染函数 |
| indent | Number | 22 | 缩进距离（px） |
| uiType | String | 'default' | UI 类型：`'default'`、`'menu'` |
| expandIcon | String | 'z_zhankai-1_normal' | 展开时的图标 |
| collapseIcon | String | 'z_shouqi-1_normal' | 收缩时的图标 |
| nodeContentAdaptive | Boolean | false | 节点内容是否自适应 |
| width | String/Number | '' | 树宽度 |
| showEllipsis | Boolean | true | 超出宽度是否显示省略号 |

## 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| nodeselect | (data, node) | 节点被选中时触发 |
| nodeexpand | (data, node, flag) | 节点展开时触发 |
| nodecollapse | (data, node, flag) | 节点收缩时触发 |
| node-click | (data, node) | 节点点击时触发 |
| node-drag-start | (node, event) | 拖拽开始时触发 |
| node-drag-enter | (draggingNode, dropNode, event) | 拖拽进入目标节点时触发 |
| node-drag-leave | (draggingNode, dropNode, event) | 拖拽离开目标节点时触发 |
| node-drag-over | (draggingNode, dropNode, event) | 拖拽经过目标节点时触发 |
| node-drag-end | (draggingNode, dropNode, dropType, event) | 拖拽结束时触发 |
| node-drop | (draggingNode, dropNode, dropType, event) | 拖拽放置时触发 |
| update:data | Array | 数据更新时触发 |

## 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 自定义节点内容，作用域插槽参数 `{ node }` |

## 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| filter | (value) | 对树节点进行筛选 |
| getCheckedNodes | (leafOnly) | 获取选中的节点数组 |
| getCheckedKeys | (leafOnly) | 获取选中的节点 key 数组 |
| getHalfCheckedNodes | — | 获取半选状态的节点数组 |
| getHalfCheckedKeys | — | 获取半选状态的节点 key 数组 |
| setCheckedNodes | (nodes, leafOnly) | 设置选中节点 |
| setCheckedKeys | (keys, leafOnly) | 设置选中节点的 key 数组 |
| getCurrentSelected | — | 获取当前选中的节点 |
| setCurrentSelected | (keys) | 设置当前选中节点 |
| setUnselected | — | 取消所有选中 |
| appendNode | (data, parentData) | 追加子节点 |
| removeNode | (data, flag) | 移除节点 |
| updateNode | (data, newData) | 更新节点数据 |
| insertBefore | (data, refData) | 在指定节点前插入 |
| insertAfter | (data, refData) | 在指定节点后插入 |
| collapseNodeByKey | (keys) | 根据 key 收缩节点 |
| expandNodeByKey | (keys) | 根据 key 展开节点 |
| getTreeData | — | 获取拖拽后的树形数据 |
| updateTreeData | (arr) | 更新源数据 |
