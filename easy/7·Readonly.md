### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00007-easy-readonly/README.zh-CN.md)
---
#### 🗝 答案
```ts
type MyReadonly<T> = {
  readonly [key in keyof T] : T[key]
}
```
由于在错误用例中出现了null,也就是说C只能是`boolean`,所以此处得加以类型限制