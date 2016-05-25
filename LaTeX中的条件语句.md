# 条件判断

## 方法1

1. 用`\newif`自定义一个条件语句；

2. 为条件变量设置一个值(set a value);

3. 就可以使用啦

   - 举个例子

     ```
     \newif \ifpaper
     \papertrue
     \ifpaper
       % balabala A
      \else
        %balabal B
      \fi
     ```

   需要注意一点，`\ifpaper`中其实**paper**是条件变量名，因此在set value的时候，必须使用`papertrue`或者`paperfalse`，注意，**前缀可都是paper（也就是条件变量名）**。

   ## 方法2

   使用`etoolbox`，举个例子

   ```
   \newtoggle{paper}
   \toggletrue{paper}
   \iftoggle{paper}{
     % balabala A
    }{
      %balabal B
    }
   ```

   ​

   ​

   ​

   ​