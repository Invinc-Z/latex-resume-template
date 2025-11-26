# LaTeX个人简历模板

---

## 引言

该模板来源于billryan的[resume](https://github.com/billryan/resume)和PM-Hu的[My_resume](https://github.com/PM-Hu/My_resume)，使用xelatex编译。简历整体的布局没有改动，主要是细节处的变化，包括一些对`cls`文件的DIY和`tex`文件一些格式的实现等。可以看作是对参考模板的一种不完全的实例化。

---

## 仓库地址以及实现效果

[仓库地址](https://github.com/Invinc-Z/latex-resume-template)

![LaTeX个人简历模板](https://invinc-z-drawing-bed.oss-cn-shanghai.aliyuncs.com/img/image-20251126180310755.png)

---

## 实现细节

### 姓名与联系方式

默认使用的是姓名在上方、联系方式在下方的结构。

```latex
% ============================= 联系方式上下结构 ============================
\name{\Huge  \kaishu 姓名}
\basicInfo{
  \email{zhuangzhuangzhang97@gmail.com} \textperiodcentered\ 
  \phone{188-8888-8888} \textperiodcentered\ 
  \github{https://github.com/Invinc-Z}
}
```

可以注释掉这种方式选择左右结构或左右结构带照片的布局方式。

```latex
% ============================= 联系方式左右结构 ============================
\begin{tabular*}{\textwidth}{@{\extracolsep{\fill}} l l}
\multirow[c]{3}{*}[-0.05in]{\Huge\kaishu 姓名}
    & \email{zhuangzhuangzhang97@gmail.com} \\
    & \phone{188-8888-8888} \\
    & \github{https://github.com/Invinc-Z} \\
\end{tabular*}
```

![姓名与联系方式左右结构](https://invinc-z-drawing-bed.oss-cn-shanghai.aliyuncs.com/img/image-20251126180624701.png)

```latex
% ============================= 联系方式左右结构带照片 ============================
\begin{tabular*}{\textwidth}{l @{\hspace{6.8cm}} r|l}
\multirow[c]{3}{*}[-0.05in]{\Huge\kaishu 姓名}
&  \multirow{3}{*}{
    \includegraphics[width=1.5cm]{avatar}
}
& \email{zhuangzhuangzhang97@gmail.com} \\
& & \phone{188-8888-8888} \\
& & \github{https://github.com/Invinc-Z} \\
\end{tabular*}
```

![姓名和联系方式左右结构带照片](https://invinc-z-drawing-bed.oss-cn-shanghai.aliyuncs.com/img/image-20251126180802481.png)

这里，姓名和照片之间的距离通过`\hspace{}`来动态调整。

### 字体

如果对当前内容字体不满意，想要**添加自己的字体**，选中命令`\fangzheng`或者`\kaishu`，将其改为**你想要的字体名称**。**你想要的字体**可以来源于：

- **系统字体**
- **自己添加**

> 由于调用了`zh_CN-Adobefonts_external`宏包，下面的中文字体，可以在全文中**直接使用**：
>
> - 宋体，`\songti`
> - 黑体，`\heiti`
> - 楷书，`\kaishu`
> - 仿宋，`\fangsong`
> - 方正，`\fangzheng`
>
> 想要自己添加喜欢的字体怎么办？以方正字体为例：
>
> 1. 将下载的字体文件，`fangzheng.ttf`，放到文件夹`..\fonts\zh_CN-Adobe`下
> 2. 打开`zh_CN-adobefonts_external.sty`
> 3. 添加命令，写入字体：`\setCJKfamilyfont{fangzheng}{fangzheng.ttf}`
> 4. 命名字体为`fangzheng`：`\newcommand*{\fangzheng}{\CJKfamily{fangzheng}} % 方正`
> 5. 保存，关闭，就可以在`*.tex`中使用方正字体了

### fontawesome6

更新图标字体为fontawesome6，可以`texdoc fontawesome6`查看`fontawesome6.pdf`，`Ctrl+F` 搜索图标名称，获得使用命令。

---

## 参考模板

- <https://github.com/billryan/resume>

- <https://github.com/PM-Hu/My_resume>

---
