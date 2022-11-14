### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00004-easy-pick/README.zh-CN.md)
---
#### 🗝 答案
```ts
type MyPick<T, K extends keyof T> = {
  [key in K]: T[key] 
}
```
#### 📑 知识点
```ts
// ts中的Pick:从Type中选取一系列的属性，这些属性来自于Keys（字符串字面量或字符串字面量的联合类型），用这些属性构成新的type
Pick<Type, Keys>
// 示例:
type Test = {
  name: string;
  age: number;
  salary?: number;
};

//pick
type picked = Pick<Test, "name" | "age">;
// 结果
// type picked = {
//     name: string;
//     age: number;
// }
```
---

`K extends keyof T`用来获取T类型的所有键类型
```ts
interface test {
  a: string;
  b: number;
}
type Keys = keyof test; // 等效于 "a" | "b"
```
`in`操作符用来遍历类型