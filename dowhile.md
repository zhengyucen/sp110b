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
### 心得
前面一直測一直跑出
```{r}
skip(=) got (null) fail!
Assertion failed!

Program: D:\sp\03-compiler\03a-compiler\compiler.exe
File: compiler.c, Line 44
```
的錯誤,後來想到do while的while還有個;要處理,skip後就成功了
