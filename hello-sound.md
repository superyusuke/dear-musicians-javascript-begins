# Hello Sound

初めてプログラミング言語を学習する際には、よく「Hello World」と呼ばれるタイプのコードを書くことになる。 "Hello World" とスクリーンに表示するプログラムだ。

しかし本書は音楽家のための本なので、"Hello Sound" アプリケーションを作ることにしよう。実行するとすぐに音がなるアプリケーションだ。

```javascript
const audioContext = new AudioContext()
const osc = audioContext.createOscillator()
osc.type = 'sine'
osc.frequency.value = 880
osc.connect(audioContext.destination)
osc.start()
```

このコードを実行すると、シンプルなサイン波が聞こえる。

実行するためには、以下のリンクをクリックしてほしい。ブラウザが別ページを開いて、

Demo \([https://codesandbox.io/s/zk178nl21p](https://codesandbox.io/s/zk178nl21p)\)

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



