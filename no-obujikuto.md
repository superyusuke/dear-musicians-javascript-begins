# 値の種類: 数値、文字列、オブジェクト、配列

JavaScript に限らず、プログラミング言語では値を扱う。`100` という数値や、`'Nakanishi'` という文字列や、`{ name: 'Nakanishi', id: 1}` というオブジェクトだ。オブジェクトは初登場。これらについて詳しくみていこう。

### 値の種類はなぜ必要か

値になぜ種類があるのか。簡単にいえば、処理をする際の法則が、値の種類によって異なるからだ。

次のコードを見て欲しい。一見どちらも同じ `100 + 100` のように見えるが、最初のものは「本当の数値の足し算」で、二つ目のものは「`100`」という「文字列」を合成したものだ。同じ `+` という演算子 \(operator\) でも、値の種類によって処理がかわり、当然結果も変わる。だから、値を宣言するときには、どのような種類を作ろうとしているのか、正確に見極め、そのための手法を使う。

```javascript
// この結果は 200 という数値になる
const sum = 100 + 100

// この結果は '100100' という文字列になる
const strings = `100` + `100`
```

### 数値 Number

まず最初に取り上げるのは数値だ。普通に数字を書けば、それが数値になる。数値に対しては、`= + - / %` といった一般的な処理をすることができる。

```javascript
const a = 1 + 2 // 結果は 2 が a に代入される
const b = 2 - 3 // 結果は -1 が b に代入される
const c = 6 / 2 // 結果は 3 が c に代入される (割り算)
const d = 3 / 2 // 結果は 1 が d に代入される (余りの計算)
```

### 文字列

文字列は `'文字列'` のようにシングルクオテーションもしくは、`"文字列"` のようにダブルクオテーションで囲うことで、囲まれた範囲が文字列になる。シングルでもダブルでもかまわないが、基本的にはどちらか一方を使う。\(特殊な事情を除けば\)

文字列は `+` を使うとつなげることができる。

```javascript
const name = 'Nakanishi'
const dialogue = '私の名前は' + name + 'です。'

// '私の名前はNakanishiです。' という文字列が出力される
console.log(dialogue)

```

### オブジェクト

数値、文字列は、一つの変数 = 箱の中に、一つの値しかしまうことができない。しかしオブジェクトは「仕切りがあるジュエリーボックス」のような値だ。オブジェクトを使えば、変数の箱の中に、さらに仕切りがある箱 = オブジェクトをしまうことができる。

![&#x30B8;&#x30E5;&#x30A8;&#x30EA;&#x30FC;&#x30DC;&#x30C3;&#x30AF;&#x30B9;&#x306F;&#x3001;&#x4ED5;&#x5207;&#x308A;&#x304C;&#x3042;&#x3063;&#x3066;&#x3001;&#x8907;&#x6570;&#x306E;&#x5024;&#x304C;&#x5165;&#x3063;&#x3066;&#x3044;&#x308B;](.gitbook/assets/opened-jewelry-box-picjumbo-com.jpg)

Object は以下のようにして作ることができる。まずは `{}` を作る。これが箱を表しているようなものだ。

そして箱の中に仕切りを作って、その仕切られた各スペースに値をしまっていこう。`key?` という部分が、仕切りの名前だ。そしてその仕切りにしまう値は `仕切りの名前: 値` という形で収納する。`仕切りの名前: 値` で1セットだ。ジュエリーボックスを仕切って、そこに一つのジュエリーをしまった。

これが以下のコードでは 3つあることになる。それぞれの部屋は「`,`」で仕切る。`,` を忘れないように気をつけて。そうじゃないと、部屋は仕切られず、ジュエリーボックは散らかったままで、エラーが出る。

一連の過程を通して、この Object というジュエリーボックスには、「三箇所スペース」があって、「それぞれに別のジュエリー」がしまわれている。[https://codesandbox.io/s/m7oo9772o9](https://codesandbox.io/s/m7oo9772o9)

```javascript
const object = {
  key1: 'value1',
  key2: 'value2',
  key3: 'value2',
}

console.log(object)

// key1 という名前の仕切りの中身にアクセスする
// 'value1' と表示される
console.log(object.key1)

// key2 という名前の仕切りの中身にアクセスする
// 'value2' と表示される
console.log(object.key2)

// key3 という名前の仕切りの中身にアクセスする
// 'value3' と表示される
console.log(object.key3)

```

ではこのジュエリーボックス全体を取り出すのではくて、ある特定の部屋にしまわれたジュエリーを取り出すにはどうしたらいいだろうか。

その場合には `object.key1` のようにして、`.` でつなぐ。そう！`audioContext.createOscillator()` や `osc.type` という形で我々はすでに見たことがある！これはオブジェクトの各部屋にアクセスしていたのだ！

### osc.type = 'sine' は何をしていたのか

これで `osc.type = 'sine'` が何をしていたのか、理解するのに一歩近づいた。

簡単にいえばこんな風になっていたのだ。  
[https://codesandbox.io/s/1qj3zlnkvj](https://codesandbox.io/s/1qj3zlnkvj)

```javascript
const osc = {
    type: 'sawtooth',
    name: 'osc1'
}

osc.type = 'sine'

console.log(osc.type) // 'sine' と出力される
```

`osc` というオブジェクトの `type` という部屋にしまわれていた値を、 `'sine'` に変更していたのだ！オブジェクトの各部屋にアクセスして、値を取り出すだけではなくて、値を変更することももちろんできる。オブジェクトの各部屋が変数のようになっているから、変数と同じ作業はだいたいできる。

### オブジェクトの部屋から値を「取り出す」のと「値をしまう」操作の違いは？

オブジェクトの各部屋から値を取り出すのも、値をしまうのも、似たような `.` の記号でで処理をしているように見えるかもしれない。整理しよう。

[https://codesandbox.io/s/wqpy3xqw05](https://codesandbox.io/s/wqpy3xqw05)

```javascript
const osc = {
  type: 'sawtooth',
  name: 'osc1',
}

// 値を取り出す
console.log(osc.type) // 'sawtooth' と出力される

// 値をしまう
osc.type = 'sine'

console.log(osc.type) // 'sine' と出力される

const variable1 = 'Hi' // 値をしまう
console.log(variable1) // 値を取り出す

```


