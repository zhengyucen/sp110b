## genEnglish.c

### 亂數函示庫
```{r}
#include "rlib.h" 
```
### 空白隔開防止黏住
```{r}
  V();
  printf(" ");
  NP();
```
### 隨機取字
```{r}
void N() {
  printf("%s", randSelect(n, 2));
}

void V() {
  printf("%s", randSelect(v, 2));
}

void DET() {
  printf("%s", randSelect(det, 2));
}
```
### 使他每次執行不一樣
```{r}
int main() {
  timeSeed();
  S();
}

```