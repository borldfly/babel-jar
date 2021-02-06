将ES6转换成ES5的基本配置内容

1.安装babel相关的包:
babel-cli
babel-preset-2015
babel-preset-react //按react标准打包
babel-preset-stage-(0~4)

2.新增.babelrc配置文件
{
    "preset": [
        "es2015"
    ],
    "plugins": []
}

3.设置默认打包路径
在package.json文件里设置默认打包路径
打包单文件
babel index.js -o index1.js
或
babel src -out-file index1.js

按路径打包
babel src -d dist
或
babel src --out-dir dist

scripts: {
    "build": "babel src -d dist"
}

解决每次提交都要输入账号密码的问题(如果加了global则表示所有仓库都不用在提交前输入账号密码)  
git config credential.helper store [--global]