### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00898-easy-includes/README.zh-CN.md)
---
#### 🗝 答案
```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U]
```
#### 📑 知识点
`ts`中可使用扩展运算符,但是需要数组,所以可以使用`extends`进行约束