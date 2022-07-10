---
title: Vue.js
description: Vue.js라는 언어는 무엇일까?
slug: start-Vue
date: 2022-02-10
image: 
categories:
    - Vue.js
tags:
    - Vue.js공부
---

---
## Component Registration
   vue component 를 global component로 만들기

```javascript
import Vue from 'vue'
import upperFirst from 'lodash/upperFirst'
import camelCase from 'lodash/camelCase'

const requireComponent = require.context(
  '.', false, /base-[\w-].vue$/
)

requireComponent.keys().forEach(fileName => {
  // Get component config
  const componentConfig = requireComponent(fileName)

// Get PascalCase name of component
  const componentName = upperFirst(
    camelCase(fileName.replace(/^\.\//, '').replace(/\.\w+$/, ''))
  )

// Register component globally
  Vue.component(componentName, componentConfig.default || componentConfig)
})
```
## Module Registration
vuex module 등록

```javascript
import camelCase from 'lodash/camelCase'
const requireModule = require.context('.', false, /\.js$/)
const modules = {}

requireModule.keys().forEach(fileName => {
  // Don't register ths file as a vuex module
  if (fileName === './index.js') return

  const moduleName = camelCase(fileName.replace(/(\.\/|\.js)/, ''))
  modules[moduleName] = {
    namespaced: true,
    ...requireModule(fileName)
  }
})
export default modules
```

## Single-Root Components
template 안에 root element가 하나 있어야 한다. 하지만 이것이 불필요하게 느껴질 경우에 functional component를 이용해서 처리하는 방법이 있다.

```javascript
<template>
  <ul>
    <NavBarRoutes :routes="persistentNavRoutes"/>
    <NavBarRoutes 
      v-if="logedIn"
      :routes="persistentNavRoutes"
    />
    <NavBarRoutes
      v-else
      :routes="persistentNavRoutes"
    />
  </ul>
</template>

[NavBarRoutes component]

export default {
  functional: true,
  render(h, {props}) {
    return props.routes.map(route =>
      <li key={route.name}>
        <router-link to={route}>
          {route.title}
        </route-link>
      </li>
    )
  }
}
```
## Transparent Wrappers
inheritAttrs, vm.$attrs, vm.$listeners를 이용하면 wrapper component를 쉽게 만들 수 있다.

@focus 부분에 .native를 붙이면 자식 컴포넌트에서 vm.$listeners 로 전달 받지 못하기 때문에 붙이면 안된다.

```javascript
<BaseInput
  placeholder="Waht's your name?"
  @focus="doSomething"
/>

[BaseInput component]

<template>
  <label>
    {{ label }}
    <input
      V-bind="$attrs"
      :value="value"
      v-on="listeners"
    ></input>
  </label>
</template>

<script>
export default {
  inheritAttrs: false,
  computed: {
    listeners() {
      return {
        ...this.$listeners
        input:event =>
          this.$emit('input', event.target.value)
      }
    }
  }
}
</script>
```

참고 영상 : https://youtu.be/7lpemgMhi0k?t=2
    
