### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00014-easy-first/README.zh-CN.md)
---
#### 🗝 答案
```ts
// 第一种
type First<T extends any[]> = T extends [] ? never : T[0]
// 第二种
type First<T extends any[]> = T['length'] extends 0 ? never : T[0]
// 第三种
type First<T extends any[]> = T extends [infer First, ...infer Rest] ? First : never
```

