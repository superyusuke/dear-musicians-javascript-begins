# Web Audio API

少しプログラミングの専門用語に慣れたところで、最初にサイン波を鳴らしたコードの、最初の部分を見ていこう。次の二行だ。

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

繰り返しになるが audioContext に頼んで oscillator を作ってもらい、それが `osc` という変数にしまわれた。DAW の場合と少し違うのは、DAW であれば作ったものは DAW の中にしまわれるが、`audioContext` の場合はそうではなくて、作られたものをしっかり変数に\(ここでは `osc` に\)しまってあげなくてはいけないということだ。

単に次のように実行しただけでは、oscillator は作成されるが、作成されたものは空中に消えてしまう。これではダメだ。変数にしっかり収納しよう。

```javascript
audioContext.createOscillator()
```

### Oscillator に値を設定する

さて、3 行目から 4行目は、oscillator の設定をしている。見た通りだが、3 行目では oscillator の波形をサイン波にしている。4 行目は周波数を 880 Hz に設定している。`audioContext.createOscillator()` の場合には `audioContext` に頼んでいるわけだが、今回は `osc` に頼んでいる。

```javascript
const audioContext = new AudioContext()
const osc = audioContext.createOscillator()
osc.type = 'sine'
osc.frequency.value = 880
osc.connect(audioContext.destination)
osc.start()
```

`audioContext.createOscillator()` の場合は、それによって作られたものを変数に収納するように注意を促したが、今回の `osc.type` と `osc.frequency.value` ではその結果を変数にしまっていないが、いいのだろうか。結論から言えばこれで良い。

DAW に例えるのであれば、Synth を作ったときには新たなものができるが、Synth の波形や周波数を変更する場合には、特に新しいものはできない。あくまで今あるものの設定を変更しているからだ。だから変数にしまう必要はない。

### audioContext.destination と connect

さて次に進もう。次のコードの 1 行目は、`osc` を `audioContext.destination` に `connect` \(接続\) している。`audioContext.destination` はなんだろう？

```javascript
osc.connect(audioContext.destination)
osc.start()
```

これは DAW でいえば、最終出力先だ。各トラックをこの出力先につなげることで、音が聞こえる。もしここにつながっていなければ、トラックで再生した音は聞こえない。それが `audioContext.destination` だ。`osc` を最終出力先につなげてあげなくては、再生しても音は聞こえない。

### osc.start\(\) でオシレーターを再生する

やっとこれで音が出る。`audioContext` から作成した `osc` に波形と周波数を設定して、最終出力先の `audioContext.destination` に `connect` したので、最後に `.start()` を `osc` にお願いしよう！

```javascript
osc.start()
```

880 Hz のサインはが再生された。

### 少なくとも意味はわかった

ここまでで少なくともコードの意味はわかったはずだ。

でも、`.` でつなぐことで JavaScript のプログラミングとしては、正確には何をしているんだろうか。`new` もなんのためにあって、何をしているのだろう。

この疑問に応えるためには、Object, Class, Construnctor 等、JavaScript の基礎的なことについて理解する必要がある。

