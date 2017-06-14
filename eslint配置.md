## 配置eslint的目的：在sublime text3编译代码保存时候，自动显示语法错误与代码书写不规范问题

### 在sublime编辑器里面采用eslint代码规范校验报错 
推荐观看[http://www.jianshu.com/p/c94db34e525b]

### 1.必要的依赖

 ```
 npm install -g eslint/babel-eslint/eslint-plugin-html/eslint-config-standard/eslint-plugin-standard/eslint-plugin-promise
 (依次安装)
 ```
    
 在全局与项目局部都安装 

`npm install --save-dev eslint/babel-eslint/eslint-plugin-html/eslint-config-standard/eslint-plugin-standard/eslint-plugin-promise`

### 2.测试依赖是否安装完全，eslint test.js（自定义一个不规范的文件.js .vue）会提示一些未安装的依赖包
   ```
   npm install -g/--save-dev  eslint-plugin-import/eslint-plugin-node
   (可能会检测出上面这些包未安装)
   ```
 
### 3.直到 eslint test.js 能正确检测代码会显示几个报错，则说明你的依赖包已经安装完全，可以正确进行代码规范检测了

### 4.接下来，需要对sublime-text进行相关包的安装：
   按ctrl+shift+P 打开包仓库 输入 'install package'安装下面2个包
    ```
    install package sublimeLinter/sublimeLinter-contrib-eslint
    ```
### 5.sublime-text 的sublimeLinter配置package setting里面的setting user(max电脑) [可选操作]
```
{
    "user": {
        "debug": true,
        "delay": 0.25,
        "error_color": "D02000",
        "gutter_theme": "Packages/SublimeLinter/gutter-themes/Default/Default.gutter-theme",
        "gutter_theme_excludes": [],
        "lint_mode": "save only",
        "linters": {
            "eslint": {
                "@disable": false,
                "args": [],
                "excludes": []
            },
            "jshint": {
                "@disable": false,
                "args": [],
                "excludes": []
            }
        },
        "mark_style": "outline",
        "no_column_highlights_line": false,
        "passive_warnings": false,
        "paths": {
            "linux": [],
            "osx": [
                "/usr/local/bin/node"
            ],
            "windows": []
        },
        "python_paths": {
            "linux": [],
            "osx": [],
            "windows": []
        },
        "rc_search_limit": 3,
        "shell_timeout": 10,
        "show_errors_on_save": true,
        "show_marks_in_minimap": true,
        "syntax_map": {
            "html (django)": "html",
            "html (rails)": "html",
            "html 5": "html",
            "javascript (babel)": "javascript",
            "magicpython": "python",
            "php": "html",
            "python django": "python",
            "pythonimproved": "python"
        },
        "tooltip_fontsize": "1rem",
        "tooltip_theme": "Packages/SublimeLinter/tooltip-themes/Default/Default.tooltip-theme",
        "tooltip_theme_excludes": [],
        "tooltips": false,
        "warning_color": "DDB700",
        "wrap_find": true
    }
}
```

### 6.设置检验报错方式：sublime-text里面文件点右键sublimeLinter设置lint mode 选择 save only ，保存时候可见


### 7.配置.eslintrc文件（可见eslint官网）
推荐配置：打开文件对应的命令行 eslint --intit  => use a popular style => standard => javascropt

然后生成一个.eslintrc。js在根目录

推荐修改

// http://eslint.org/docs/user-guide/configuring
```
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
    'arrow-parens': 0,
    // allow async-await
    'generator-star-spacing': 0,
    // allow debugger during development
    'no-debugger': process.env.NODE_ENV === 'production' ? 2 : 0
  }
}
```
