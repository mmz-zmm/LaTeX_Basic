# 参考文献的写法

1. 假设已经有了`myreference.bib `文件, 其格式为:

   ```
   @article{MartinDSP00,
   author = "A. Martin and M. Przybocki", 
   title = "The {NIST} 1999 speaker recognition evaluation --- an overview",
   journal = "Digital Signal Processing",
   volume = "10", 
   pages = "1--18", 
   year = "2000",}
   ```

2. 若使用` bibtex package`, 当需要引用文献的时候,在正文里加入:

   ```
   \bibliographystyle{style_name}  %style_name = plain, unsrt
   \bibliography{myreference}      % myreference.lib 文件 
   ```

3. 若使用 biblatex package,     则需要以下命令:

   ```
   \usepackage[
              style = numeric]{biblatex}            % set in the preamble
   \addbibresource{myreference.lib} % add reference file(.bib),also set in the preamble
   \printbibliography               % inside the document, before the document end
   \printbibliography[title = References] % 将参考文献的标题变为 References

   ```

   # 引用的相关信息

   1. 关于`package:hyperref`的一些注意事项：

      ```
      \usepackage[colorlinks]{hyperref}
      ```

      当使用`\cite`的时候，不同类型的引用会显示不同的颜色，**对于PDF的阅读非常方便，但是确实打印时不希望出现的情况**。

   2. 如果采用`colorlinks = True`的设置，则可以同时自定义

      ```
      linkcolor [red]   % [] 中为默认颜色
      anchorcolor [black]
      citecolor [green]
      filecolor [cyan]
      menucolor [red]
      runcolor [cyan - same as file color]
      urlcolor [magenta]
      allcolors -- use this if you want to set all links to the same color
      ```

      **注意，**我在用武汉大学的论文模板时，就用到了`allcolors = black`的选项，这样在打印的时候就不会出现花花绿绿。

   ​

   ​