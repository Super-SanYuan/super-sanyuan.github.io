---
title: 实现一个简单的 Form 表单组件
date: 2019-12-30 14:26:20
tags:
  - Vue
categories:
  - Vue
---

&emsp;&emsp;本文主要通过实现一个简单的 Form 组件来学习 Vue 中相关知识点.

### 相关知识点

- v-model 指令的实质
- 父子组件定义属性传值 props \$emit
- 子孙组件传值 provide inject
- slot 插槽
- 在生命周期中监听自定义事件

### 需求分析

- 数据双向绑定
- 单个规则校验
- label
- error 错误提示
- 数据获取
- 数据传递
- 全局校验

### 组件拆分(单一性)

- Input 组件
- FormItem 组件
- Form 组件

### 组件功能划分

---

> Input 组件

数据双向绑定  
触发规则校验

---

> FormItme 组件

label  
prop  
error

---

> Form 组件

数据模型持有  
校验规则持有  
数据传递  
全局校验

---

### 功能实现

```javascript
// Input 组件
<template>
  <div>
    <input type="text" :value="value" @input="onInput" />
  </div>
</template>

<script>
/**
 * 职能
 * 1.双向绑定
 * 2.触发校验
 */
export default {
  name: 'KInput',
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  methods: {
    onInput(e) {
      // v-model 监听 input
      this.$emit('input', e.target.value)
      // 触发校验
      this.$parent.$emit('validate')
    }
  }
}
</script>
```

```javascript
// FormItem 组件
<template>
  <div>
    <label v-if="label">{{ label }}</label>
    <slot />
    <span v-show="error">{{ error }}</span>
  </div>
</template>

<script>
/**
 * 职能
 * 1.校验
 * 2.label
 * 3.error
 */
import Schema from 'async-validator'
export default {
  inject: ['form'],
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      error: ''
    }
  },
  mounted() {
    this.$on('validate', () => {
      this.validate()
    })
  },
  methods: {
    validate() {
      /**
       * 引入 sync-validate 插件
       * 获取校验规则与校验值
       */
      const value = this.form.model[this.prop]
      const rule = this.form.rules[this.prop]

      const schema = new Schema({ [this.prop]: rule })

      return schema.validate(
        { [this.prop]: value.trim() },
        errors => (this.error = errors ? errors[0].message : '')
      )
    }
  }
}
</script>
```

```javascript
// Form 组件
<template>
  <div>
    <slot />
  </div>
</template>

<script>
/**
 * 职能
 * 1.数据持有丶传递
 * 2.全局校验
 */
export default {
  props: {
    model: {
      type: Object
    },
    rules: {
      type: Object
    }
  },
  provide() {
    return {
      form: this
    }
  },
  methods: {
    validate(cb) {
      /**
       * 全局校验
       * 获取所有子组件
       * 找到带有prop验证的
       * 调用子组件自身的校验方法
       */
      const tasks = this.$children
        .filter(item => item.prop)
        .map(item => item.validate())

      Promise.all(tasks)
        .then(() => cb(true))
        .catch(() => cb(false))
    }
  }
}
</script>
```

```javascript
// 测试
<template>
  <div>
    <KFrom ref="form" :model="model" :rules="rules">
      <KFormitem lable="用户名" prop="uname">
        <KInput v-model="model.uname"></KInput>
      </KFormitem>
      <KFormitem lable="密码" prop="pwd">
        <KInput v-model="model.pwd"></KInput>
      </KFormitem>
      <KFormitem>
        <button @click="submit">校验</button>
      </KFormitem>
    </KFrom>
  </div>
</template>

<script>
import KFrom from './KForm'
import KFormitem from './KFormitem'
import KInput from './KInput'
export default {
  components: { KFrom, KFormitem, KInput },
  data() {
    return {
      model: {
        uname: '',
        pwd: ''
      },
      rules: {
        uname: [{ required: true, message: '用户名不能为空' }],
        pwd: [{ required: true, message: '密码不能为空' }]
      }
    }
  },
  methods: {
    submit() {
      this.$refs.form.validate(isValidate => {
        if (isValidate) {
          alert('校验通过')
        } else {
          alert('校验失败')
        }
      })
    }
  }
}
</script>
```
