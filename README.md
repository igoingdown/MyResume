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

## Quick Start
### For Mac users
To Use my latex resume source templates, several steps to go:
1. download and install mactex: [download from here](http://www.texts.io/support/0001/). 
1. config **TexShop** App as [configuration instruction](https://liam.page/2014/11/02/latex-mactex-chinese-support/).
1. clone repo: `git clone https://github.com/igoingdown/MyResume.git`. 
1. go to project dir: `cd resume_template`. 
1. open and edit latex file `main.tex` with **Texshop** app pre-installed.
1. replace the picture `photo.png` by your own photo with filename unchanged.
1. in **Texshop** app, click the button bellow to compile the tex file.
![IMG](/docs/images/button.png)
1. if no bugs in latex source file, you will get a resume named `main.pdf`. Congratulations!



### For terminal users
1. download and install **basic tex**: [download from here](http://www.texts.io/support/0001/).
1. install moderncv and ctex with `tlmgr`: `sudo tlmgr update && sudo tlmgr install moderncv ctex multibib` 
1. clone repo: `git clone https://github.com/igoingdown/MyResume.git`.
1. go to project dir: `cd resume_template`.
2. edit tex file `main.tex` with whatever text editor you like.
3. replace the picture `photo.png` by your own photo with filename unchanged.
4. run `pdflatex main.tex` to compile the tex file.
5. if no bugs in latex source file, you will get a resume named `main.pdf`. Congratulations!


### For Windows users
1. 使用WPS将我的简历pdf文档(`template.pdf`)转为word
1. 使用WPS在word中修改排版字体和格式，换成自己的内容
1. 使用WPS将word文件导出为pdf就是你自己的简历啦！





## Example



![IMG](/docs/images/resume_shortcut.png)



## Personal Info

#### 微信



![IMG](/docs/images/wechat.png)



#### 微信公众号



![IMG](/docs/images/001-minglangwanwu.png)



#### 邮箱

**Zhao Mingxing** - *[zhaomingxingdl@gmail.com](mailto:zhaomingxingdl@gmail.com)* 

