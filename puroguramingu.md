# 変数\(variable\)

音楽の比喩で説明するだけではなくて、そろそろプログラミングの専門用語を紹介したい。

まずは「変数」\(variable\) だ。以下のコード

```javascript
const audioContext = new AudioContext()
```

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

