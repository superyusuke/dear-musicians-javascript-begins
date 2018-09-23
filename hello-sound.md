# Hello Sound

初めてプログラム言語を学習する際に、よく紹介されるのが「Hello World」と呼ばれるコードで、これを最初に書くことが多い。これは "Hello World" とスクリーンに表示するプログラムだ。

しかし本書は Web Audio API を使ってサウンドを創造することを目的としているので、"Hello Sound" アプリケーションを作ることにしよう。実行するとすぐに音がなるアプリケーションだ。

Demo \([https://codesandbox.io/s/zk178nl21p](https://codesandbox.io/s/zk178nl21p)\)

```javascript
// AudiocContext は Browser に組み込まれたオブジェクト
// そのオブジェクトから new operator によって、audioContext インスタンスを作成する
// このインスンタンスが WebAudioAPI に関わる全ての操作のインターフェイス(入り口)となっている
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

このコードを実行すると、シンプルなサイン波が聞こえる。

Web Audio API は、Browser API と呼ばれる種類の API で、ブラウザに組み込まれている。ので、当然だが Node では使えない。



