# 変数\(variable\)

音楽の比喩で説明するだけではなくて、そろそろプログラミングの専門用語を紹介したい。

まずは「変数」\(variable\) という用語を覚えてほしい。変数というのは、値を保存する箱だ、と一般的に説明される。箱なのだから、まずは箱を「作る」指示をする必要がある。そして箱を作ったら、その箱に「値をしまう」指示も必要になるだろう。

具体的にどんなふうに使うのか、説明しよう。以下のコードを見てほしい。

```javascript
const audioContext = new AudioContext()
```

### 変数の宣言\(Declaring Variables\) = 箱を作る

`const` と書くことで、これから変数の箱を作ることを「宣言」する。その変数の箱の名前は「audioContext」と決めることにした。だから `const audioContext` と書いてある。この部分までで、 "audioContext" という名前の箱ができた。

### 代入\(Assignment\) = 値を箱にしまう

その後ろに続く `=` を含む部分が、箱に値を入れる過程だ。`audioContext` という箱に、`=` 以降の値をしまってやろうとしている。何を入れるかと言えば、`new AudioContext()` の実行結果だ。この実行がなんなのかは少し難しいので後で詳しく説明することにしよう。とにかく今覚えてほしいのは、実行した結果が、`=` という記号のおかげで、`audioContext` という箱の中に吸い込まれて、しまわれるということだ。変数の箱に値をしまうためには、`=` を使う。この箱に値をしまう作業を「代入」という。

```javascript
// AudiocContext は Browser に組み込まれたオブジェクト
// そのオブジェクトから new operator によって、
// audioContext インスタンスを作成する

// このインスンタンスが WebAudioAPI に関わる
// 全ての操作のインターフェイス(入り口)となっている
const audioContext = new AudioContext()

// audioContext のメソッドを用いて、oscillator を作成する
const osc = audioContext.createOscillator()

// oscillator の波形を sine に変更する
osc.type = 'sine'

// oscillator の周波数(frequency)の値(value)を 880 に変更する
osc.frequency.value = 880

// oscillator を destination(目的地 = マスターアウトプットに接続する)
osc.connect(audioContext.destination)

// oscillator を start = 再生 する
osc.start()
```

