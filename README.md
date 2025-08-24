#  MyResume

## Repo Struct
```shell
├── docs
│   └── images     # 图片，用于README
│       ├── button.png
│       └── resume_shortcut.png  # 简历模板截图
├── resume_template # 中文版工作简历模板project
│   ├── main.tex    # 中文版工作简历模板源码
│   └── photo.png   # 中文版工作简历模板使用的个人照片
├── zhaomingxing_resume_for_job_en # 我的英文版工作简历project
└── zhaomingxing_resume_for_job_zh # 我的中文版工作简历project
```

## For Mac(terminal) users

*以下流程通过 AI 生成，prompt 为：我在 GitHub 上找到了一个 LaTeX 项目，希望clone 到本地并编译生成 pdf 文件，如何操作，我的计算机是 mac 系统，新电脑，没有配置过开发环境，答案写到一个 markdown 文件中*

* 安装 Homebrew（包管理器）打开终端（Terminal），粘贴以下命令并回车，按提示输入密码，完成安装。

```
/bin/bash -c "\$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
* 安装 Git（用于克隆项目）在终端中执行：

```
brew install git
```

* 安装 LaTeX 编译环境，推荐安装 MacTeX（完整套件）：


```
brew install --cask mactex
```


*  克隆本项目

```
git clone https://github.com/用户名/项目名.git  # 替换为实际复制的链接
```

* 进入项目文件夹：



```
cd $HOME/github/MyResume/zhaomingxing_resume_for_job_zh

```

* 替换个人信息

编辑 `main.tex` 并替换照片 `photo.png`

* 编译

```
xelatex main.tex
```



## Example



![IMG](/docs/images/resume_shortcut.png)



## Personal Info

#### 微信



![IMG](/docs/images/wechat.png)



#### 微信公众号



![IMG](/docs/images/001-minglangwanwu.png)



#### 邮箱

**Zhao Mingxing** - *[zhaomingxingdl@gmail.com](mailto:zhaomingxingdl@gmail.com)* 

