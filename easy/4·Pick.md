### ð [é¢ç®æè¿°](https://github.com/type-challenges/type-challenges/blob/main/questions/00004-easy-pick/README.zh-CN.md)
---
#### ð ç­æ¡
```ts
type MyPick<T, K extends keyof T> = {
  [key in K]: T[key] 
}
```
#### ð ç¥è¯ç¹
```ts
// tsä¸­çPick:ä»Typeä¸­éåä¸ç³»åçå±æ§ï¼è¿äºå±æ§æ¥èªäºKeysï¼å­ç¬¦ä¸²å­é¢éæå­ç¬¦ä¸²å­é¢éçèåç±»åï¼ï¼ç¨è¿äºå±æ§æææ°çtype
Pick<Type, Keys>
// ç¤ºä¾:
type Test = {
  name: string;
  age: number;
  salary?: number;
};

//pick
type picked = Pick<Test, "name" | "age">;
// ç»æ
// type picked = {
//     name: string;
//     age: number;
// }
```
---

`K extends keyof T`ç¨æ¥è·åTç±»åçææé®ç±»å
```ts
interface test {
  a: string;
  b: number;
}
type Keys = keyof test; // ç­æäº "a" | "b"
```
`in`æä½ç¬¦ç¨æ¥éåç±»å  

`type ValueOf<T> = T [keyof T]`è·åææå¼çèåç±»å
```ts
interface Todo1 {
  title: string
  description: string
  completed: boolean
  meta: {
    author: string
  }
}
type ValueOf<T> = T [keyof T]
type test = ValueOf<Todo1> // 'string' | 'boolean' | { author:'string' }
```