# LaTeX中的图与表

1. Float的概念：如图、表之类不希望在一页上中断的内容，将其采用放在一个container中，这个container就构成了一个float，默认的float包括图、表。

2. 建议对图表使用**[htbp]**指定浮动的位置

3. 每页上最多只能放两张图，因此为了避免所有的图堆积在最后一页，造成排版上的不美观，建议把图表分散，可以把**要引用的图表提前导入，之后采用`\ref`进行引用**，但用注意，**可能会引起阅读上的不便**

4. 图表与正文之间距离的调整

   - `\textfloatsep`：Space below **top** `[t]` and above **bottom** `[b]` floats is managed via the length；

   -  `\intextsep`：Space above and below **here** `[h]` floats is managed via the length；

   - `\floatsep` — distance between two floats;

     - 举例来说，

     ```
     \setlength{\intextsep}{10pt} % Vertical space above & below [h] floats
     \setlength{\textfloatsep}{10pt} % Vertical space below (above) [t] ([b]) floats
     \setlength{\abovecaptionskip}{10pt}
     \setlength{\belowcaptionskip}{5pt}
     ```

   - ![raGsR](F:\User\Documents\Work\Coding\LaTeX\picture\raGsR.png)

​	4.  **需要注意的是**，当调整`floats``之间的距离时，我采用以上设置的时候，**并不起作用**。