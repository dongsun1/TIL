# Vuex 사용법

1. 먼저 store/index.js 파일을 만든 후 아래 코드를 작성한다.

```js
export const state = () => ({
  list: []
})

export const mutations = {
  add(state, text) {
    state.list.push({
      text,
      done: false
    })
  },
  remove(state, { todo }) {
    state.list.splice(state.list.indexOf(todo), 1)
  },
  toggle(state, todo) {
    todo.done = !todo.done
  }
}
```

그럼 Nuxt에서 아래와 같은 형태로 재컴파일 해준다. 

```js
new Vuex.Store({
  state: () => ({
    counter: 0
  }),
  mutations: {
    increment(state) {
      state.counter++
    }
  },
  modules: {
    todos: {
      namespaced: true,
      state: () => ({
        list: []
      }),
      mutations: {
        add(state, { text }) {
          state.list.push({
            text,
            done: false
          })
        },
        remove(state, { todo }) {
          state.list.splice(state.list.indexOf(todo), 1)
        },
        toggle(state, { todo }) {
          todo.done = !todo.done
        }
      }
    }
  }
})
```

2. 실제 Vue.js 컴포넌트(페이지)에서 사용하는 예제는 아래와 같다.

```vue
<template>
  <ul>
    <li v-for="todo in todos" :key="todo.text">
      <input :checked="todo.done" @change="toggle(todo)" type="checkbox">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
    </li>
    <li><input @keyup.enter="addTodo" placeholder="할일 목록 입니다."></li>
  </ul>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  computed: {
    todos () {
      return this.$store.state.todos.list
    }
  },
  methods: {
    addTodo (e) {
      this.$store.commit('todos/add', e.target.value)
      e.target.value = ''
    },
    ...mapMutations({
      toggle: 'todos/toggle'
    })
  }
}
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
```

Store에 사용 되는 소스코드는 `index.js` 파일 하나에 몰아서 넣어도 되며 혹은 4개의 `actions.js`, `getters.js`, `index.js`,`mutations.js` 파일로 각각 나누어서 작성해도 자동으로 인식 된다. 모듈은 폴더로 나누면 되며 루트 모듈도 마찬가지이다. 유지보수 측면에서는 나누는 것이 약간 유리 할 것이다. 자신의 프로젝트 규모에 맞게 적절하게 구성 하면 된다.