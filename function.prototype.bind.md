### 核心问题： 解决函数、对象等内部 this指向变化引起的报错

#### 经典案例：封装vue的组件时候，有一些交互需要用到第三方ui库 如element.ui，调用方式往往有this.$nofity(xxx)

#### 经典代码： 在父组件中传入，子组件执行方法

//父组件中传入

``` 
<template>
  <div class="hello">
    <btnGroup :rules="rules" :actions="actions"></btnGroup>
  </div>
</template>

<script>
import btnGroup from '@/components/buttonGroup'
export default {
  name: 'hello',
  data () {
    return {
      rules:[
      {
        name:'alertment',
        title:'弹窗'
      },
      {
        name:'info',
        title:'提示'
      }
      ],
      actions:{
        alertment(){
          console.log('alert')
          this.$notify.info({
            title: '消息',
            message: '这是一条消息的提示消息'
          });
        },
        info(){
          console.log('info')
          this.$notify({
            title: '成功',
            message: '这是一条成功的提示消息',
            type: 'success'
          })
        }
      }
    }
  },
  components:{
    btnGroup
  },
  created() {
    console.log('created',this)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

```

//子组件中调用

```
<template>
	<div>
		<span v-for="item in rule">
			<el-button @click="btnClick(item.name)">{{item.title}}</el-button>
		</span>
	</div>
</template>

<script>
export default {

  name: 'buttonGroup',

  data () {
    return {
    	rule:this.rules,
    	action:this.actions
    }
  },
  methods:{
  	btnClick(name) {
  		console.log('name',name)
  		this.action[name].bind(this)()//将父组件中的this指向重新指向vueComponent，再执行,(一定要先bind后执行)
  	}
  },
  props:{
  	rules:{
  		type:Array
  	},
  	actions:{
  		type:Object
  	}
  }
}
</script>

<style lang="css" scoped>
</style>

```


