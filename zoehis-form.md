# zoehis-form / zoehis-form-item / zoehis-form-row 组件文档

> 组件来源：`@zoesoft.com.cn/his-component-vue` 组件库

## 概述

这是一组表单相关组件，提供了一套完整的表单解决方案：

- **zoehis-form**：表单容器组件，管理表单数据、校验规则和所有表单项
- **zoehis-form-item**：表单项组件，支持标签展示、表单校验、错误提示等功能
- **zoehis-form-row**：表单行组件，用于 isRows 模式下嵌套表单行布局

三个组件配合使用，支持数据驱动、规则校验（基于 async-validator）、重置、清除校验等能力。

## 基础用法

```vue
<template>
  <zoehis-form
    :data="formData"
    :rules="formRules"
    labelWidth="100px"
    type="single"
    ref="formRef">
    <zoehis-form-item label="姓名" prop="name" required>
      <el-input v-model="formData.name" />
    </zoehis-form-item>
    <zoehis-form-item label="年龄" prop="age">
      <el-input-number v-model="formData.age" />
    </zoehis-form-item>
    <zoehis-form-item>
      <el-button type="primary" @click="submitForm">提交</el-button>
      <el-button @click="resetForm">重置</el-button>
    </zoehis-form-item>
  </zoehis-form>
</template>

<script>
export default {
  data() {
    return {
      formData: { name: '', age: 0 },
      formRules: {
        name: [{ required: true, message: '请输入姓名', trigger: 'blur' }]
      }
    }
  },
  methods: {
    submitForm() {
      this.$refs.formRef.validate((valid) => {
        if (valid) console.log('校验通过')
      })
    },
    resetForm() {
      this.$refs.formRef.resetForm()
    }
  }
}
</script>
```

---

## zoehis-form

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| data | Object | {} | 表单数据对象 |
| type | String | 'single' | 表单类型，可选值：`single`（单列）、`multiple`（多列） |
| rules | Object | {} | 表单校验规则对象 |
| gutter | Number | 30 | 栅格间隔，单位为 px |
| labelWidth | String | '50px' | 标签宽度 |
| disabled | Boolean | false | 是否禁用整个表单 |
| showMessage | Boolean | true | 是否显示校验错误信息 |
| span | String / Number | - | 表单项默认所占栅栏数目 |
| offset | Number | - | 表单项默认偏移量 |
| gutterSide | Boolean | true | 是否保留两边的间隔 |
| labelPosition | String | 'left' | 标签对齐方式 |
| labelWidthFixed | Boolean | false | 是否强制固定文本标签宽度（不建议使用） |
| isRows | Boolean | false | 是否采用嵌套 row col 布局（不建议使用） |
| space | Number / String | - | 表单项上下间距 |
| labelStyle | Object | {} | 标签自定义样式 |

### 方法（Methods）

| 方法名 | 参数 | 说明 |
|--------|------|------|
| resetForm | - | 重置所有表单项的值和校验状态 |
| clearValidate | (props: Array) | 清除指定字段的校验状态，不传参数则清除所有 |
| validate | (callback: Function, rules: Object, isBefore: Boolean, isOriginalValidate: Boolean) | 校验整个表单，callback 接收 (valid, invalidFields) |
| validateField | (props: Array, callback: Function) | 校验部分指定字段 |

### 事件（Events）

| 事件名 | 参数 | 说明 |
|--------|------|------|
| validate | (prop: String, valid: Boolean, message: String) | 每个表单项校验完成后触发 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置 zoehis-form-item 或 zoehis-form-row 子组件 |

---

## zoehis-form-item

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| data | Object | {} | 表单数据（一般不传，继承自父级 form） |
| span | String / Number | - | 表单项所占栅栏数目，继承父级 form 的 span |
| rules | Array | [] | 行内校验规则，优先级高于父级 form 的 rules |
| required | Boolean | false | 是否必填，为 true 时自动添加必填校验 |
| prop | String | '' | 绑定字段名称，用于数据获取和校验 |
| label | String | '' | 标签文本 |
| labelWidth | String / Number | - | 标签宽度，继承父级 form 的 labelWidth |
| showMessage | Boolean | true | 是否显示校验错误信息 |
| line | Boolean | false | 是否渲染为横线分隔 |
| offset | Number | - | 偏移量，继承父级 form 的 offset |
| labelPosition | String | - | 标签对齐方式，继承父级 form 的 labelPosition |
| labelWidthFixed | Boolean | false | 是否强制固定文本标签宽度（不建议使用） |
| space | Number / String | - | 表单项上下间距，继承父级 form 的 space |
| labelStyle | Object | {} | 标签自定义样式，与父级 form 的 labelStyle 合并 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置表单控件 |
| extra | 额外内容插槽（仅 labelPosition 为 top 时显示） |
| error | 自定义错误提示内容插槽，覆盖默认错误信息 |

---

## zoehis-form-row

### 属性（Props）

| 属性名 | 类型 | 默认值 | 说明 |
|--------|------|--------|------|
| span | String / Number | - | 表单项所占栅栏数目 |
| offset | Number | - | 偏移量 |
| labelPosition | String | - | 标签对齐方式 |
| labelWidth | String | - | 标签宽度，继承父级 form 的 labelWidth |
| labelWidthFixed | Boolean | - | 是否强制固定文本标签宽度（不建议使用） |
| space | Number / String | - | 表单项上下间距 |

### 插槽（Slots）

| 插槽名 | 说明 |
|--------|------|
| default | 默认插槽，放置 zoehis-form-item 子组件 |
