# About vuex

## learning tips [https://github.com/yelingfeng/vuex-tutorial]

### some tips from me in using vue-cli+webpack

#### 1.0 structure
```
                                modules1.js （模块存储中心）
 store  <  modules(模块文件夹)<  modules2.js （模块存储中心）
           getters.js（获取数据中心）
           actions.js（操作数据中心）
           store.js（入口）
```

#### 1.1 main.js
```
   import store from '@/vuex/store.js'
   ~~~~
   new Vue({
      el: '#app',
      router,
      store,
      template: '<App/>',
      components: { App }
   })
   
```

#### 1.2 store.js
```
import Vuex from 'vuex'
import Vue from 'vue'
import getters from './getters'
import module1 from './modules/module1.js'
import module2 from './modules/module2.js'
Vue.use(Vuex)
const store = new Vuex.Store({
	modules: {
		module1,
		module2
	},
	getters
})
export default store

```

### 1.3 getters.js(调用时候要在computed)

```
export const isEmptySearchKey = (store) => {
    return store.search.searchKey !== ""
}
或者

const getter = {
  getName:name => state.module1.name,
  getAge: age => state.module.age
}
export default getter
```

#### 1.4 modules1.js

```

const form = {
  state: {
    price: 0, // 会员信息售卡金额
    memberInfo: []
  },
  mutations: {
    SET_CARDINFO: (state, info) => {
      state.price = info.Product.price
    },
    SET_MEMBERINFO: (state, info) =>{
      state.memberInfo = info
    }
  },
  actions: {
    // 会员级别选项改变数据
    setCardInfo ({ commit }, value) {
      commit('SET_CARDINFO', value)
    },
    setMemberInfo ({ commit }, value) {
      commit('SET_MEMBERINFO', value)
    }
  }
}
export default form

```
#### 1.5 调用

```
	import { mapGetters } from 'vuex'
	
	
	computed: {
	    ...mapGetters([
	      'memberInfo' //  可以用this.memberInfo取到     
	   ])
	}
	
```

