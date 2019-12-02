# 用ESLint来规范Typescript代码

## 安装依赖

```bash
npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

这三个依赖分别是：

- [eslint](https://www.npmjs.com/package/eslint): ESLint的核心代码
- [@typescript-eslint/parser](https://www.npmjs.com/package/@typescript-eslint/parser)：ESLint的解析器，用于解析typescript，从而检查和规范Typescript代码
- [@typescript-eslint/eslint-plugin](https://www.npmjs.com/package/@typescript-eslint/eslint-plugin)：这是一个ESLint插件，包含了各类定义好的检测Typescript代码的规范

## 配置
安装好这3个依赖包之后，在根目录下新建`.eslintrc.js`文件，该文件中定义了ESLint的基础配置，一个最为简单的配置如下所示：

```js
module.exports = {

    parser:  '@typescript-eslint/parser', //定义ESLint的解析器
    extends: ['plugin:@typescript-eslint/recommended'],//定义文件继承的子规范, enable all the recommended rules for our plugin
    plugins: ['@typescript-eslint'],//定义了该eslint文件所依赖的插件
    env:{                          //指定代码的运行环境
        browser: true,
        node: true,
    }
}
```

- 在ts项目中必须执行解析器为`@typescript-eslint/parser`，才能正确的检测和规范TS代码
- `env`环境变量配置，形如`console`属性只有在`browser`环境下才会存在，如果没有设置支持`browser`,那么可能报`console is undefined`的错误。

## Usage with Prettier

Install [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) to disable our code formatting related rules:

```js
{
  "extends": [
    "plugin:@typescript-eslint/recommended",
    "prettier",
    "prettier/@typescript-eslint"
  ]
}
```

Note: Make sure you have `eslint-config-prettier@4.0.0` or newer.
