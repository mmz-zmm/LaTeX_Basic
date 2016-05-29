1. 问题背景：在使用中文版的武汉大学博士论文Latex模板进行**英文**书写时，如何调整文本的字体？(采用XeLaTeX编译)

   解决方法：

   - **设置全局字体** \usepackage{fontspec}`：

      ```
      \setmainfont[<font features>]{<name of font>} % sets the roman font
      \setsansfont[<font features>]{<name of font>} % sets the sans font
      \setmonofont[<font features>]{<name of font>} % sets the monospace font
      ```

   ​             举个例子：  

   - **设置局部字体**：定义一个新的*font family*：

     ````
      \newfontfamily\myfont[<font features>]{<name of font>}
     %%-----------------------------------------------------
     %% you can use the command like that:
     {\myfont ...} % or
     \begingroup
       \myfont ...
     \endgroup    % or
     \newenvironment{myfont}{\myfont}{\par}  % set a selfdefine environment
     \begin{myfont}
       Some text in the new font.
     \end{myfont} xxxxxxxxxx1 1
     ````

     定义了一个变换`\myfont`，当使用这个命令时，可以将选定的文字的字体换成设定值。

     ​

2. TeX 字体的属性:

   - 编码（encoding）、族（family）、系列（series）、形状（shape）和字体大小；

   - main/sans/mono 分别为三种family，即衬线/无衬线/等宽字体；

   - 举个例子：

     ```
     \documentclass[12pt]{article}
     \usepackage{xeCJK,fontspec}

     \setmainfont{Times New Roman}
     \setsansfont{Helvetica}
     \setmonofont{Courier New}
     \setCJKmainfont{simsun.ttc} %宋体
     \setCJKsansfont{msyh.ttf} %微软雅黑
     \setCJKmonofont{FZYTK.ttf} %方正姚体

     \begin{document}

     \large\rmfamily\selectfont Lorem ipsum dolor sit amet 中文字体

     \large\sffamily\selectfont Lorem ipsum dolor sit amet 中文字体

     \large\ttfamily\selectfont Lorem ipsum dolor sit amet 中文字体

     \end{document}

     作者：Louis Stuart
     链接：https://www.zhihu.com/question/20563044/answer/25649002
     来源：知乎
     著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
     ```

     ​


