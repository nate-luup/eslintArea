# 在VSCode中集成ESLint配置

为了开发方便我们可以在VSCode中集成ESLint的配置，使得代码在保存或者代码变动的时候自动进行ESLint的fix过程。

首先需要安装VSCode的ESLint插件，安装插件完毕后，在`settings.json`文件中修改其配置文件为：

```json
{
       "eslint.enable": true,  //是否开启vscode的eslint
       "eslint.autoFixOnSave": true, //是否在保存的时候自动fix eslint
       "eslint.options": {    //指定vscode的eslint所处理的文件的后缀
           "extensions": [
               ".jsx",
               ".js",
               ".vue",
               ".ts",
               ".tsx"
           ]
       },
       "eslint.validate": [     //确定校验准则
           "javascript",
           "javascriptreact",
           {
               "language": "html",
               "autoFix": true
           },
           {
               "language": "vue",
               "autoFix": true
           },
           {
               "language": "typescript",
               "autoFix": true
           },
           {
               "language": "typescriptreact",
               "autoFix": true
           }
       ]
}
```

**主要注意的有两点：**

- eslint.options中可以通过configFile属性来执行eslint规范的绝对路径，默认会向上查找，在根路径中指定。
- eslint.validate中必须通过{ language: XXX}的形式来指定typescript和typescriptreact
