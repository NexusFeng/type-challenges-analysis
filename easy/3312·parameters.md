### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/03312-easy-parameters/README.zh-CN.md)
---
#### 🗝 答案
```ts
type MyParameters<T extends (...args: any) => any> = T extends (
  ...args: infer x
) => any
  ? x
  : [];
```
#### 📑 知识点
内置工具类型 `Parameters` 的作用是拿到函数入参的类型，并且把所有入参的类型存放到一个元组中去
```ts
const foo = (arg1: string, arg2: number): void => {};

type S = Parameters<typeof foo>;
// type S = [arg1: string, arg2: number]
```
关于[infer](https://www.jianshu.com/p/707a304d7752)
```ts
type InferArray<T> = T extends [...infer U] ? U : never;

type typeArr = InferArray<[1,'2',true]> // [number, string, boolean]
```