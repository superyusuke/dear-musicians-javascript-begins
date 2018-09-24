# 関数 \(function\)

[https://codesandbox.io/s/94248pj49r](https://codesandbox.io/s/94248pj49r)

```javascript
// function1 という変数に関数をしまう
// () => {} の部分が値としての関数を
// 作っている
// {} の中身が、実行される内容
const function1 = () => {
  // この中身の部分が実行される内容
  console.log('function1')
}

// 関数を実行するには、
// 関数が入った変数の最後に () をつける
function1()

const function2 = () => {
  // この中身の部分が実行される内容
  // 当然だが複数行あってもいい
  const sum = 1 + 2
  console.log(sum, 'function2')
}

function2()

// argument の部分が引数
// 関数を実行する際に、値を渡すことができる
const function3 = (argument) => {
  // 渡された値は {} の中で使うことができる
  console.log(argument, 'function3')
}

function3('this is argument')

// 関数の中で return をすると、
// 関数を実行した際に、
// return に与えた値が
// 「返って」くる
const function4 = () => {
  return 'return!!!'
}

// 値が返ってくる
console.log(function4(), 'function4')

// return がない場合は undefined が返る
// undefined = 何もないよ
console.log(function1(), 'function1 no return')

const function5 = (num) => {
  return num * 2
}

// 5 * 2 で 10 が返ってくる
console.log(function5(5), 'function5 argument = 2')

// 10 * 2 で 20 が返ってくる
console.log(function5(10), 'function5 argument = 10')

```



