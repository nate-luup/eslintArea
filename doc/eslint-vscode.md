# 在VSCode中集成ESLint

为了开发方便我们可以在VSCode中集成ESLint的配置，使得代码在保存或者代码变动的时候自动进行ESLint的fix过程。

首先需要安装VSCode的ESLint插件，安装插件完毕后，在`settings.json`文件中修改其配置文件为：

## 插件

[VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

## 配置


```json
{
    "eslint.enable": true,  //是否开启vscode的eslint
    "eslint.autoFixOnSave": true, //是否在保存的时候自动fix eslint

    "eslint.validate": [     //确定校验准则
        "javascript",
        "javascriptreact",
        {
            "language": "html",
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

### 配置项说明

- `eslint.enable`: enable/disable ESLint. Is enabled by default.
- `eslint.autoFixOnSave` - enables auto fix on save.
- `eslint.validate` - an array of language identifiers specify the files to be validated.

**注意：** `eslint.validate` 中必须通过 `{ language: XXX }` 的形式来指定 `typescript` 和 `typescriptreact`
