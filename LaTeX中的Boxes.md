开宗明义，

> LaTeX builds up its pages by pushing around **boxes**.

1. 对于一个字母来说，它也有Box，分别有以下三个控制参数：

    ![210px-Texcharbox.svg](F:\User\Documents\Work\Coding\LaTeX\picture\210px-Texcharbox.svg.png)

2. ```
   \makebox[width][pos]{text}  % make 一个Box，简写为\mbox
   \framebox[width][pos]{text} % make 一个带框的Box，简写为\fbox
   \raisebox{lift}[height][depth]{text} % 能控制Box的水平和竖直位置
   ```

有几点需要补充：

- `pos`选项可以是 c （ `center` ），l（`flushleft），`r（`flushright`），s（`spread the text to fill the box`）
- `\raisebox`选项中的lift表示的应该是偏移baseline的距离，实际上就是raise or lower text。