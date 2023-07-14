# README Contributors Action

这个项目旨在提供一种简单的方式将项目/仓库的所有贡献者汇总在一张表格里并显示在`README`文件中。

为什么需要一个贡献者名单？这是一种鼓励，也是一种表示友好和感谢的方式。

## 效果演示

<!-- readme: collaborators,contributors -start -->
<table>
<tr>
    <td align="center">
        <a href="https://github.com/hilinxinhui">
            <img src="https://avatars.githubusercontent.com/u/72953081?v=4" width="100;" alt="hilinxinhui"/>
            <br />
            <sub><b>Xinhui Lin</b></sub>
        </a>
    </td></tr>
</table>
<!-- readme: collaborators,contributors -end -->

## 如何使用

### 生成token

1. 在GitHub`Settings`中新建token（classic即可），勾选`repo`和`workflow`权限
2. 在目标仓库中添加`Secrets`

### 部署action

1. 在项目中创建`.github/workflows/main.yml`（文件名随意）
2. `main.yml`中的内容看起来像这样：

```yml
on:
    push:
        branches:
            - main

jobs:
    contrib-readme-job:
        runs-on: ubuntu-latest
        name: A job to automate contrib in readme
        steps:
            - name: Contribute List
              uses: akhilmhdh/contributors-readme-action@v2.3.6
              env:
                GITHUB_TOKEN: ${{ secrets.CONTRIBUTE_TOKEN }}
```

注意：

- `branches`字段可能不是`main`
- `GITHUB_TOKEN`字段和[上一步](#生成token)生成的`token_name`保持一致

### 修改README

在`README.md`文件中添加：

```HTML
<!-- readme: collaborators,contributors -start -->
<!-- readme: collaborators,contributors -end -->
```

即可。

注意每次有人员变更时仓库会新增一个提交记录，像这样：

`docs(contributor): contrib-readme-action has updated readme`

本地仓库提交新内容时记得`git pull`。

## 许可

本仓库使用[MIT](./LICENSE)协议。

## 致谢

- [contributors-readme-action](https://github.com/akhilmhdh/contributors-readme-action.git)
- [all-contributors](https://github.com/all-contributors/all-contributors.git)
- [image-shield](https://github.com/badges/shields)