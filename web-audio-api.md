# Web Audio API

サインは少しプログラミングの専門用語に慣れたところで、最初にサイン波を鳴らしたコードの、最初の部分を見ていこう。次の二行だ。

```javascript
const audioContext = new AudioContext()
const osc = audioContext.createOscillator()
```

まずは `const` によって変数を宣言する。その変数の名前は `audioContext` だ。そしてその変数に、`new AudioContext()` の実行結果を代入している。これはなんだろうか。

### new AudioContext\(\) は DAW のプロジェクトを立ち上げるようなもの

まずは比喩で説明したい。これを実行することで、DAW の一つのプロジェクトが立ち上がる。そしてそれが `audioContext` の中にしまわれる。

この `audioContext` を使って、オシレーターを作ったり、エフェクトを作ったり、マスターの出力先を作ったり、ありとあらゆる作業をする。ちょうど DAW の一つのプロジェクトの中で、シンセを作ったり、トラックを作ったり、ボリュームの操作をしたりするのと全く同じだ。DAW と同じなのだから、`audioContext` は特殊な事情がなければ、一個だけあればいい。

### audioContext = DAW の 1 プロジェクトから、オシレーターを作る

次のコードは、先ほど作った `audioContext` からオシレーターを作るコードだ。

```javascript
const osc = audioContext.createOscillator()
```

注目してほしいのは、`.` によって `audioContext` と `createOscillator()` がつなぎ合わされる形になっているところだ。これは、`audioContext` の `createOscillator()` という操作を実行してくれ、という意味になる。DAW に例えるとこんな感じのコードになるだろう。

```javascript
DAW.createSynth()
```

上のコードは、「DAWよ、Synth を作ってくれ」という意味になる。`DAW` に `createSynth()` を実行させているわけだ。これと同じことが、`audioContext.createOscillator()` にもいえる。`audioContext` に Oscillator を作らせているわけだ。そして、作られたものが `osc` という変数に収納される。

もう一度、二行目を見てみよう。

```javascript
const osc = audioContext.createOscillator()
```

繰り返しになるが audioContext に頼んで oscillator を作ってもらい、それが `osc` という変数にしまわれた。DAW の場合と少し違うのは、DAW であれば作ったものは DAW の中にしまわれるが、`audioContext` の場合はそうではなくて、作られたものをしっかり変数にしまってあげなくてはいけないということだ。

単に次のように実行しただけでは、oscillator は作成されるが、作成されたものは空中に消えてしまう。これではダメだ。変数にしっかり収納しよう。

```javascript
audioContext.createOscillator()
```

#### Oscillator に値を設定する

さて、3 行目から 4行目は、oscillator の設定をしている。見た通りだが、3 行目では oscillator の波形を

```javascript
const audioContext = new AudioContext()
const osc = audioContext.createOscillator()
osc.type = 'sine'
osc.frequency.value = 880
osc.connect(audioContext.destination)
osc.start()
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

```

