# 核心问题： 解决函数、对象等内部 this指向变化引起的报错

## 经典案例：封装vue的组件时候，有一些交互需要用到第三方ui库 如element.ui，调用方式往往有this.$nofity(xxx)

### 经典代码  在父组件中传入 子组件执行的方法
//父组件中传入
` data () {
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
`

//子组件中调用

`
  	btnClick(name) {
  		console.log('name',name)
  		this.action[name].bind(this)()//将父组件中的this指向重新指向vueComponent，再执行,(一定要先bind后执行)
  	}
`


