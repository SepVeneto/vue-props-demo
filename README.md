1. 通过props传递引用类型(对象)的数据更新
2. $set的作用
3. 频繁调用$set会不会影响性能
### 父组件状态更新
example:
```js
<form-vue :value="formData" />
```

父组件触发子组件更新
```js
this.formData = {
  name: 'test'
}

```

虽然不会由于props的值变化更新子组件，但是由于子组件在渲染过程中访问过`value.name`，触发了`value`也就是`this.formData`的`getter`中的依赖收集，所以当触发父组件的`formData`的`setter`时，会通知子组件进行更新。

```js
this.formData.name = 'test'
```

所以其实本质都是在子组件渲染的时候访问过

### 子组件状态更新
example:
```html
<template>
  <input v-model="value.name" />
  <input v-model="value.age" />
</template>
<script>
export default {
  props: {
    value: Object
  }
}
</script>
```

```js
defineReactive(props, key, value, () => {
  if (!isRoot && !isUpdatingChildComponent) {
    warn(
      `Avoid mutating a prop directly since the value will be ` +
        `overwritten whenever the parent component re-renders. ` +
        `Instead, use a data or computed property based on the prop's ` +
        `value. Prop being mutated: "${key}"`,
      vm
    )
  }
})
```

能触发响应式
