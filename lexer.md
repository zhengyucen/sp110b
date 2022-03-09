## lexer.c

### 印一次將各個token取掉
```{r}
int main(int argc, char * argv[]) {
  readText(argv[1], code, sizeof(code)-1);
  puts(code);
  lex(code);
  dump(tokens, tokenTop);
}
```

### 連續取字元或數字
```{r}
if (*p == '\0') return NULL;
  if (*p == '"') {
    p++;
    while (*p != '"') p++;
    p++;
    type = Literal;
  } else if (*p >='0' && *p <='9') { // 數字
    while (*p >='0' && *p <='9') p++;
    type = Int;
  } 
  ```
## 剩下的單一字元或關鍵字
```{r}
  else if (isAlpha(*p) || *p == '_') { // 變數名稱或關鍵字
    while (isAlpha(*p) || isDigit(*p) || *p == '_') p++;
    type = Id;
  } else { // 單一字元
    p++;
    type = Char;
  }
  ```

## 主程式 每次取一個印出字串表
```{r}
void lex(char *code) {
  char *p = code;
  while (1) {
    p = next(p);
    if (p == NULL) break;
  }
}
 ```

 ## 空白字元濾掉
```{r}
 char *next(char *p) {
  while (isspace(*p)) p++;
```