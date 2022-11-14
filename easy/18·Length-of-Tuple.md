### 🔗 [题目描述](https://github.com/type-challenges/type-challenges/blob/main/questions/00018-easy-tuple-length/README.md)
---
#### 🗝 答案
```ts
type Length<T extends readonly any[]> = T['length']
```
#### 📑 知识点
ts中获取数组的长度可以通过`T['length']`来获取, 由于测试用例加了`as const`所以此时还需要增加一个`readonly`属性  
ts中的`as const`: as const 被称为 const 类型断言，const 类型断言告诉编译器，要将这个表达式推断为最具体的类型，如果不使用它的话，编译器会使用默认的类型推断行为，可能会把表达式推断为更通用的类型
```ts
// str1的类型就是str,而str2的类型是string,意味着它可以再次修改
const str1 = 'str' // str
let str2 = 'str' // string

let str3 = 'str' as const // 不可以在修改
// 对于引用类型 as const起到了很好的限制
let arr = ['str'] as const // 不可以在修改
```
测试用例中提到`typeof`,在js中,`typeof`可以用来区分引用类型和基本类型,在ts中也是如此,不过功能更强大一些
```ts
const message = {
  name: "feng",
  age: 7,
  skill: {
    js: true,
    vue: true
  },
};
interface Person {
  name: string,
  age: number,
  skill: {
    js: boolean,
    vue: boolean
  },
}
// 这种多层的数据定义interface是非常麻烦的，可以借助typeof
type Person = typeof message
type Skill = typeof message['skill']
```
