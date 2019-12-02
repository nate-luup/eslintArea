# 结合Prettier和ESLint来规范代码

## 安装依赖

```bash
npm i -D prettier eslint-config-prettier
```

- [prettier](https://www.npmjs.com/package/prettier)：prettier插件的核心代码
- [eslint-config-prettier](https://www.npmjs.com/package/eslint-config-prettier)：**解决ESLint中的样式规范和prettier中样式规范的冲突，以prettier的样式规范为准，使ESLint中的样式规范自动失效**

Add `eslint-config-prettier` to the `"extends"` array in your `.eslintrc.*`file. **Make sure to put it last**, so it gets the chance to override other configs.

If you extend a config which uses a plugin, it is recommended to add `"prettier/that-plugin"` (if available). For example, `eslint-config-airbnb` enables `eslint-plugin-react` rules, so `"prettier/react"` is needed:

- [eslint-plugin-prettier](https://www.npmjs.com/package/eslint-plugin-prettier)：将prettier作为ESLint规范来使

To integrate this plugin with `eslint-config-prettier`, you can use the "recommended" configuration:

Add `plugin:prettier/recommended` as the **last extension** in your `.eslintrc.*`:

```js
{
  "extends": ["plugin:prettier/recommended"]
}
```

**This does three things:**

- Enables `eslint-plugin-prettier`.
- Sets the `prettier/prettier` rule to "error".
- Extends the `eslint-config-prettier` configuration.

## 添加prettier配置文件
然后在项目的根目录下创建`.prettierrc.js`文件：

```js
module.exports =  {
    "printWidth": 120,
    "semi": false,
    "singleQuote": true,
    "trailingComma": "all",
    "bracketSpacing": false,
    "jsxBracketSameLine": true,
    "arrowParens": "avoid",
    "insertPragma": true,
    "tabWidth": 4,
    "useTabs": false
};
```

## 修改eslint配置文件
接着修改`.eslintrc.js`文件，引入`prettier`：

```js
module.exports = {
    parser:  '@typescript-eslint/parser',
    extends:[
        'plugin:@typescript-eslint/recommended',
        'plugin:react/recommended',
        'prettier',
        'prettier/@typescript-eslint'
    ],
    plugins: ['@typescript-eslint'],
    settings: {
        "react": {
            "pragma": "React",
            "version": "detect"
        }
    },
    parserOptions: {
        "ecmaVersion": 2019,
        "sourceType": 'module',
        "ecmaFeatures":{
            jsx:true
        }
    },
    env:{
        browser: true,
        node: true,
    }
```

上述新增的extends的配置中：
- prettier/@typescript-eslint：使得@typescript-eslint中的样式规范失效，遵循prettier中的样式规范
- plugin:prettier/recommended：使用prettier中的样式规范，且如果使得ESLint会检测prettier的格式问题，同样将格式问题以error的形式抛出
