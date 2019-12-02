# husky和lint-staged构建代码工作流

首先来看husky,Husky 能够帮你阻挡住不好的代码提交和推送,首先我们在`package.json`中定义如下的script:

```js
 "scripts": {
   "lint": "eslint src --fix --ext .ts,.tsx "
}
```
接着在`package.json`定义`husky`的配置：

```js
 "husky": {
   "hooks": {
      "pre-commit": "npm run lint"
    }
},
```

我们在`git`的`hook`的阶段来执行相应的命令，比如上述的例子是在`pre-commit`这个`hook`也就是在提交之前进行`lint`的检测。

接着来看`lint-staged`，上述我们通过在`husky`的`pre-comit`这个`hook`中执行一个`npm`命令来做`lint`校验。除了定义个`npm lint`命令外，我们也可以直接通过使用`lint-staged`，来在提交前检测代码的规范。

使用`lint-staged`来规范代码的方式如下，我们修改`package.json`文件为：

```js
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{.ts,.tsx}": [
      "eslint",
      "git add"
    ]
  }
}
```
同样在git commit的时候会做lint的检测。
