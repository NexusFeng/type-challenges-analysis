### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00043-easy-exclude/README.zh-CN.md)
---
#### 🗝 答案
```ts
type MyExclude<T, U> = T extends U ? never : T
```
#### 📑 知识点
```ts
// ts内置工具类型Exclude:从UnionType中去掉所有能够赋值给ExcludedMembers的属性，然后剩下的属性构成一个新的类型
Exclude<UnionType, ExcludedMembers>
type T0 = Exclude<"a" | "b" | "c", "a">// 'b' | 'c'
```
---
ts条件类型语法如下:
```ts
// 当被检查类型(T)可以赋值给类型U时,返回类型X, 否则返回类型Y
T extends U ? X : Y
```
举几个简单的示例:
```ts
type IsNumber<T> = T extends number ? true : false
type one = IsNumber<10> // true
type two = IsNumber<'abc'> // false
```
当被检查类型时联合类型的时候,就是**分布式条件类型**,当被检查类型时'裸'类型时(没有被元组、数组、Promise、函数等包装过),运算过程会分解成多个分支
```ts
A | B | C extends U ? X : Y
// 分解为
(A extends U ? X : Y) | (B extends U ? X : Y) | (C extends U ? X : Y) 
```
TS几个内置工具类型的内部实现(Exclude/Extract/NonNullable等)也使用了条件类型
```ts
// IsNumber2中的[T]被数组包装过了，不会进行分发，直接判断[string | number] extends number[], 得到了false
type IsNumber2<T> = [T] extends number[] ? true : false
type three = IsNumber2<string | number> // false
```