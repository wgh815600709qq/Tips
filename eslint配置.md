#1.在代码运行时候对于代码规范报错，vue官网推荐时候询问eslint？yes即可

#2.在sublime编辑器里面对于代码规范报错[http://www.jianshu.com/p/c94db34e525b]

###1.必要的依赖

    `npm install -g eslint/babel-eslint/eslint-plugin-html/eslint-config-standard/eslint-plugin-standard/eslint-plugin-promise`
    
    在全局与项目局部都安装 

    `npm install --save-dev eslint/babel-eslint/eslint-plugin-html/eslint-config-standard/eslint-plugin-standard/eslint-plugin-promise`

###2.测试eslint test.js会提示一些未安装的依赖包
    npm install -g/--save-dev  eslint-plugin-import/eslint-plugin-node
    
###3.sublime-text 的sublimeLinter配置package setting里面的setting user
`{
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
}`
