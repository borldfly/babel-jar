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

修改git历史提交注释信息
1.查看历史提交记录
git log --pretty=oneline

2.查看最近提交的记录(n为最近n次提交记录)
git rebase -i HEAD~n

3.进入编辑历史记录界面，修改历史记录
pick version content
pick version1 content1
pick version2 content2
...
按i进行编辑，将要改的内容前面的pick改为edit
按esc退出编辑，按:wq退出编辑界面
输入命令：git commit --amend
显示要改的内容
按i进行修改，修改完按esc退出编辑，输入:wq退出编辑界面
再输入保存命令：git rebase --continue
直到显示 'Successfully rebased and updated xxxxx'

4.此时再次查看提交记录，命令：git log --pretty=oneline会发现记录已修改
