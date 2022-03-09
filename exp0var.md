## exp0var.c

### 分出數字和字母分別儲存
```{r}
 if (isdigit(c) || (c>='a'&&c<='z')) {
    next(); // skip c
    f = nextTemp();
    genOp1(f, c);
  } if (isdigit(c) || (c>='a'&&c<='z')) {
    next(); // skip c
    f = nextTemp();
    genOp1(f, c);
```
### 判斷括號或是否錯誤
```{r}
else if (c=='(') { // '(' E ')'
    next();
    f = E();
    assert(ch()==')');
    next();
```
### 判斷i取道多少,且部會重複
```{r}
int nextTemp() {
  static int tempIdx = 0;
  return tempIdx++;
}
```
### 判斷下一個字元在哪
```{r}
int isNext(char *set) {
  char c = ch();
  return (c!='\0' && strchr(set, c)!=NULL);
}
```
### 把下一個取掉
```{r}
char next() {
  char c = ch();
  tokenIdx++;
  return c;
}
```