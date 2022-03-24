## dowhile(c6)
### 參考老師的while以及下方return遇到;的處理方法所寫
```{r}
    else if (tk == 'Do')
    {
    next();
    a = e + 1;
    stmt();
    if (tk == While)
    {
      next();
      if (tk == '(')
        next();
      else
      {
        printf("%d: open paren expected\n", line);
        exit(-1);
      }
      expr(Assign);
      if (tk == ')')
        next();
      else
      {
        printf("%d: close paren expected\n", line);
        exit(-1);
      }
      if (tk == ';')
        next();
      else
      {
        printf("%d: semicolon expected\n", line);
        exit(-1);
      }
      *++e = BNZ;
      *++e = (int)a;
    }
     else
    {
      printf("%d: syntax errors\n", line);
      exit(-1);
    }
  }
```
### test
```{r}
#include <stdio.h>
int main()
{
    int s;
    int i;
    i = 2;
    s = 3;
    do
    {
        s = i + s;
        i = i + 1;
        printf("do while: s=%d i=%d\n", s, i);
    } while (i < 30);
    printf("s=%d i=%d\n", s, i);
    return 0;
```
### 結果
```{r}
do while: s=5 i=3
do while: s=8 i=4
do while: s=12 i=5
do while: s=17 i=6
do while: s=23 i=7
do while: s=30 i=8
do while: s=38 i=9
do while: s=47 i=10
do while: s=57 i=11
do while: s=68 i=12
do while: s=80 i=13
do while: s=93 i=14
do while: s=107 i=15
do while: s=122 i=16
do while: s=138 i=17
do while: s=155 i=18
do while: s=173 i=19
do while: s=192 i=20
do while: s=212 i=21
do while: s=233 i=22
do while: s=255 i=23
do while: s=278 i=24
do while: s=302 i=25
do while: s=327 i=26
do while: s=353 i=27
do while: s=380 i=28
do while: s=408 i=29
do while: s=437 i=30
s=437 i=30
exit(0) cycle = 947
```
### 心得想法
主要處理方式跟上個作業一樣,遇到的麻煩就是沒在enum和compile的p增加導致無法辨識
*++e = BNZ;*++e = (int)a;
BNZ:if (a!=0) goto m[pc]

