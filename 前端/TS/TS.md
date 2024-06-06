# TS知识点总结
### '!'
parentEl.value!.tagName.toLowerCase();

！表示（非空断言） 是 TypeScript 的非空断言操作符，表示开发者确信 value 不是 null 或 undefined，因此在运行时不进行这方面的检查。使用它的目的是告诉 TypeScript 编译器这里的值一定存在。 

### '??'
`
const VITE_APP_TITLE = import.meta.env.VITE_APP_TITLE ?? "V3 Admin Vite";
`
?? 操作符是空值合并操作符。它用于在左操作数为 null 或 undefined 时提供一个默认值。
如果左侧为null或者undefined时就取值右侧

### Partial
`
 const setWatermark = (text: string, config: Partial<DefaultConfig> = {}) {

 } // Partial是啥意思？
 `
 在 TypeScript 中，Partial 是一个实用工具类型，用于将某个类型的所有属性变为可选的。它定义在 TypeScript 的标准库中
 所以config中按照DefaultConfig类型中所有的类型都是可选型
