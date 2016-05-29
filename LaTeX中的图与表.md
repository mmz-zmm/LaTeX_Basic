# LaTeX中的图与表

1. Float的概念：如图、表之类不希望在一页上中断的内容，将其采用放在一个container中，这个container就构成了一个float，默认的float包括图、表。

2. 建议对图表使用**[htbp]**指定浮动的位置

3. 每页上最多只能放两张图，因此为了避免所有的图堆积在最后一页，造成排版上的不美观，建议把图表分散，可以把**要引用的图表提前导入，之后采用`\ref`进行引用**，但用注意，**可能会引起阅读上的不便**

4. 图表与正文之间距离的调整

   - `\textfloatsep`：Space below **top** `[t]` and above **bottom** `[b]` floats is managed via the length；

   - `\intextsep`：Space above and below **here** `[h]` floats is managed via the length；

   - `\floatsep` — distance between two floats;

     - 举例来说，

     ```
     \setlength{\intextsep}{10pt} % Vertical space above & below [h] floats
     \setlength{\textfloatsep}{10pt} % Vertical space below (above) [t] ([b]) floats
     \setlength{\abovecaptionskip}{10pt}
     \setlength{\belowcaptionskip}{5pt}
     ```

   - ![raGsR](F:\User\Documents\Work\Coding\LaTeX\picture\raGsR.png)

    **需要注意的是**，当调整`floats``之间的距离时，我采用以上设置的时候，**并不起作用**。

5. 合并行和列：

   - 合并行：

     ```
     \multirow{nrows}[bigstructs]{width}[fixup]{text}
     %% 要使用package{mulrow}
     %% bigstructs 和 fixup 是可选项，我用的时候都不写；
     %% width为文本宽度。如果用“*”，表示让LaTeX自行决定
     ```

   - 合并列

     ```
     \multicolumn{<no of columns>}{<column align type>}{<stuff>}
     %% <column align type> could be l,c,r(左，中，右)
     ```

6. 子图的排列方式

   - 竖直方式排列，各个图表有独立的caption（subfigures vertically）

     ```
     %% 使用minipage
     \begin{figure}
     \centering
     \begin{minipage}[c][11cm][t]{.5\textwidth}
       \centering
       \includegraphics[width=5cm,height=4.5cm]{image1}
       \caption{test figure one} % 标题1(Figure)
       \label{fig:test1}\par\vfill  %% \par and \vfill 非常关键
       \includegraphics[width=5cm,height=4.5cm]{image1}
       \caption{test figure two} % 标题2(Figure)
       \label{fig:test2}
     \end{minipage}
     \end{figure}
     ```

   - 竖直方式排列，各个图表作为子图（subfigures vertically）

     ```
     %% 使用minipage
     \usepakage{subcaption} %% 使用 subcaption
     ······
     \begin{figure}
     \centering
     \begin{minipage}[c][11cm][t]{.5\textwidth}
       \centering
       \includegraphics[width=5cm,height=4.5cm]{image1}
       \subcaption{test figure one} % 分标题(a)
       \label{fig:test1}\par \medskip \vfill  %% \par and \vfill 非常关键
       \includegraphics[width=5cm,height=4.5cm]{image1}
       \subcaption{test figure two} % 分标题(b)
       \label{fig:test2} 
     \end{minipage}
     \caption{fig:test}  % 图表总的标题
     \end{figure}
     ```

   - 水平方式排列，各个图表各有子标题(使用a,b,c编号)，并共享一个主标题

     ```
     \usepakage{graphicx}
     \usepakege{caption}
     \usepakage{subcaption}

     \begin{figure}
         \centering
         \begin{subfigure}[b]{0.3\textwidth}
             \includegraphics[width=\textwidth]{gull}
             \caption{A gull} % 子标题
             \label{fig:gull}
         \end{subfigure}

         \begin{subfigure}[b]{0.3\textwidth}
             \includegraphics[width=\textwidth]{tiger}
             \caption{A tiger} % 子标题
             \label{fig:tiger}
         \end{subfigure}

         \begin{subfigure}[b]{0.3\textwidth}
             \includegraphics[width=\textwidth]{mouse}
             \caption{A mouse}   % 子标题
             \label{fig:mouse}   
         \end{subfigure}
         \caption{Pictures of animals}\label{fig:animals}  % 主标题
     \end{figure}
     链接：  https://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions#Subfloats
     ```

   - 水平排列，共享标题的其他方式

     ```
     \begin{figure}[htbp]
     \centering
     \includegraphics{left}
     \includegraphics{right}
     \caption{The caption of figure}  %% 共享标题
     \end{figure}
     ```

   -   水平排列，各有标题(使用figure编号)（使用minipage）

     ```
     \begin{figure}[htbp]
     \centering
     \begin{minipage}[t]{0.3\textwidth}
     \centering
     \includegraphics{left}
     \caption{figure one}
     \end{minipage}

     \begin{minipage}[t]{0.3\textwidth}
     \centering
     \includegraphics{right}
     \caption{figure two}
     \end{minipage}
     \end{figure}
     链接：https://zhaoshiliang.wordpress.com/2010/07/27/%E5%A4%9A%E5%9B%BE%E6%8E%92%E7%89%88/
     ```

7. 在使用中文LaTeX模板写英文大作业的时候，出现如下状况：图和表的标题显示为中文样式，比如*表1* ，*图1*，但是我希望得到的是*Table 1*和*Figure 1*。解决方法如下：

   ```
   \usepackage[figurename = Figure,
               tablename  = Table]{caption}
   %% 使用caption package，可以做到自由的修改表格和图片的标题显示方式
   %% 如 figurename = Fig. tablename  = Tab.
   ```

   ​