## dowhile
### 參考老師的while打的
```{r}
void DOWHILE()
{
  int dowhileBegin = nextLabel();
  int dowhileEnd = nextLabel();
  emit("(L%d)\n", dowhileBegin); //記錄點
  skip("do"); 
  STMT(); //處理內部程式
  skip("while");
  skip("(");
  int e = E(); //判斷式
  emit("if not t%d goto L%d\n", e, dowhileEnd); //條件式成立則跳開
  skip(")");
  skip(";"); 
  emit("goto L%d\n", dowhileBegin);
  emit("(L%d)\n", dowhileEnd);
}

```
##### STMT()要加
```{r}
else if (isNext("do"))
    DOWHILE();
```
### 結果
```{r}
s = 0;
i = 1;
do
{
    s = s + i;
    i = i + 1;
} while (i < 10);
========== lex ==============
token=s
token==
token=0
token=;
token=i
token==
token=1
token=;
token=do
token={
token=s
token==
token=s
token=+
token=i
token=;
token=i
token==
token=i
token=+
token=1
token=;
token=}
token=while
token=(
token=i
token=<
token=10
token=)
token=;
========== dump ==============
0:s
1:=
2:0
3:;
4:i
5:=
6:1
7:;
8:do
9:{
10:s
11:=
12:s
13:+
14:i
15:;
16:i
17:=
18:i
19:+
20:1
21:;
22:}
23:while
24:(
25:i
26:<
27:10
28:)
29:;
============ parse =============
t0 = 0
s = t0
t1 = 1
i = t1
(L0)
t2 = s
t3 = i
t4 = t2 + t3
s = t4
t5 = i
t6 = 1
t7 = t5 + t6
i = t7
t8 = i
t9 = 10
t10 = t8 < t9
if not t10 goto L1
goto L0
(L1)
```
### 心得
前面一直測一直跑出
```{r}
skip(=) got (null) fail!
Assertion failed!

Program: D:\sp\03-compiler\03a-compiler\compiler.exe
File: compiler.c, Line 44
```
的錯誤,後來想到do while的while還有個;要處理,skip後就成功了
 