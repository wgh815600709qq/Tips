## 配置eslint的目的：
在sublime text3编译代码保存时候，自动显示语法错误与代码书写不规范问题

### 在sublime编辑器里面采用eslint代码规范校验报错 
推荐链接[http://www.jianshu.com/p/c94db34e525b]

### 1.必要的依赖

 ```
npm install -g eslint
npm install -g babel-eslint
npm install -g eslint-plugin-html
npm install -g eslint-config-standard
npm install -g eslint-plugin-standard
npm install -g eslint-plugin-promise
npm install -g eslint-plugin-import
npm install -g eslint-plugin-node
 (依次安装)
 ```
    

### 2.测试依赖是否安装完全，eslint  test.js（自定义一个不规范的文件.js .vue）会提示一些未安装的依赖包
```
   
   然后按步骤1全局补充安装
```
 
### 3.直到 eslint test.js 能正确检测代码会显示几个报错，则说明你的依赖包已经安装完全，可以正确进行代码规范检测了

### 4.接下来，需要对sublime-text进行相关包的安装：
   按ctrl+shift+P 打开包仓库 输入 'install package'安装下面2个包
```
    install package sublimeLinter
    install package sublimeLinter-contrib-eslint
```


### 5.设置检验报错方式：sublime-text里面文件点右键sublimeLinter设置lint mode 选择 save only ，保存时候可见


### 6.配置.eslintrc文件（可见eslint官网）
推荐配置：打开文件对应的命令行 eslint --intit  => use a popular style => standard => javascropt

然后生成一个.eslintrc.js在根目录

推荐修改

```
// http://eslint.org/docs/user-guide/configuring

module.exports = {
  root: true,
  parser: 'babel-eslint',
  parserOptions: {
    sourceType: 'module'
  },
  env: {
    browser: true,
  },
  // https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style
  extends: 'standard',
  // required to lint *.vue files
  plugins: [
    'html'
  ],
  // add your custom rules here
  'rules': {
    // allow paren-less arrow functions
    'arrow-parens': 0,                      // 关闭箭头函数强制使用小括号
    'generator-star-spacing': 0,            // 允许异步等待 async-await
    "linebreak-style": ["error", "unix"],   // 换行风格
    "quotes": [1, "single"],                // 引号类型：使用单引号
    "semi": ["error", "never"],             // 禁止分号作为语句结尾
    "eqeqeq": 0,                            // 关闭强制使用 '===' 和 '!==' 来做判断比较
    "no-unused-vars": 0,                    // 关闭强制 声明未使用变量
    "space-before-function-paren": 0,       // 关闭函数名后的空格
    "prefer-const": 0,                      // 关闭首选const
    "no-undef": 0,                          // 关闭不能使用未定义变量
    // "camelcase": 0,                         // 关闭强制驼峰命名
    // 在开发过程中允许调试器
    'no-debugger': process.env.NODE_ENV === 'production' ? 2 : 0,
  }
}

```
