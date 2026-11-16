# LESSON 3
```block
let ポイントA: Position = null
let ポイントD: Position = null
let ポイントB: Position = null
let ポイントC: Position = null
player.onChat("a", function (x, y, z) {
    ポイントA = world(x, y, z)
})
player.onChat("d", function (x, y, z) {
    ポイントD = world(x, y, z)
})
player.onChat("b", function (x, y, z) {
    ポイントB = world(x, y, z)
})
player.onChat("c", function (x, y, z) {
    ポイントC = world(x, y, z)
})
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
    火をつける(ポイントA)
    火をつける(ポイントB)
    火をつける(ポイントC)
    火をつける(ポイントD)
})

```

```template
player.onChat("run", function () {
	
})
```

## 変数と関数を使ってプログラミングしてみよう @unplugged
変数に座標を保存して、関数で火をつけよう！<br>
<img style="display: block; margin: auto;" height="40%" width="40%" src="https://i.ibb.co/kG9hb0K/l1-3-1.png">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・座標をチャットコマンドで「run x y z」(x,y,zはそれぞれ火をつけたい場所の座標)を入力して保存する<br>
・チャットで「run」と入力したら保存した座標すべてに火をつける<br>
<img style="width:100%" src="https://i.ibb.co/j8PwRtL/l1-3-2.gif"><br>

## 関数を作ろう
まずは火をつけるための関数を作りましょう<br>
<img style="width:100%" src="https://i.ibb.co/r06CvJ9/l1-3-3.png"><br>

## Step 1
高度なブロックをクリックして、`||functions.関数||`をクリックします</br>
`||functions.関数を作成する…||`をクリックして、【doSomething】を【火をつける】に入力しなおします</br>
『パラメーターを追加する』の`||agent.『Position』||`をクリックして、【position】を【座標】に入力しなおしてから完了をクリックします<br>

## Step 2
次は関数「火をつける」の中に火をつけるためのプログラムを作ります</br>
`||blocks.ブロック||`から`||blocks.ブロックを~0~0~0に置く||`を関数の中に入れます</br>
`||blocks.草ブロック||`を`||blocks.炎||`に変えます</br>
関数「火をつける 座標」の座標をドラッグして`||blocks.~0~0~0||`に重ねます<br>
```blocks
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
	
})
```

## Step 3
チャットコマンドでそれぞれのポイントの座標を保存できるようにしましょう</br>
`||player.プレイヤー||`から`||player.チャットコマンド"jump"を入力した時||`を１つ取り出し、"jump"を"a"に変えます<br>
```blocks
player.onChat("a", function () {
	
})
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
	
})



```

## Step 4
チャットコマンド"a"の⊕を３回クリックします</br>
そして、num1をクリックして変数を作成する…を選んでxに入力しなおします</br>
さらにnum2をy、num3をzに入力しなおします<br>
```blocks
player.onChat("a", function (x, y, z) {
	
})
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
	
})

```

## Step 5
座標を保存する変数を作りましょう<br>
`||variables.変数||`から`||variables.変数を作成する||`をクリックし、【ポイントA】と名前を付けてOKを押します</br>
同じようにして【ポイントB】、【ポイントC】【ポイントD】を作りましょう<br>
<img style="width:100%" src="https://i.ibb.co/8KvFJxR/l1-3-step5.png"><br>

## Step6
`||variables.変数||`から`||variables.変数 ポイントDを0にする||`を取り出し、`||player.チャットコマンド"a"を…||`の中に入れます</br>
`||variables.ポイントD||`を`||variables.ポイントA||`に変えて、`||positions.ポジション||`から`||positions.ワールド~0~0~0||`を`||variables.変数 ポイントAを0にする||`の0に重ねます<br>

## Step7
`||variables.変数||`から`||variables.x||`、`||variables.y||`、`||variables.z||`を取り出し、`||positions.ワールド~0~0~0||`の左にx、まん中にy、右にzを重ねます<br>


## Step8
保存したいポイントの座標の数だけチャットコマンドを増やしましょう</br>
`||player.チャットコマンド"a"||`の上にカーソルを合わせて右クリックをして、「複製する」を押します</br>
`||チャットコマンド"a"||`を`||チャットコマンド"b"||`にして、`||variables.ポイントA||`を`||variables.ポイントB||`にします</br>
同じようにして【ポイントC】と【ポイントD】も作ります<br>
```blocks
let ポイントA: Position = null
let ポイントD: Position = null
let ポイントB: Position = null
let ポイントC: Position = null
player.onChat("a", function (x, y, z) {
    ポイントA = world(x, y, z)
})
player.onChat("d", function (x, y, z) {
    ポイントD = world(x, y, z)
})
player.onChat("b", function (x, y, z) {
    ポイントB = world(x, y, z)
})
player.onChat("c", function (x, y, z) {
    ポイントC = world(x, y, z)
})
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
	
})


```

## Step9
`||functions.関数||`から`||functions.呼び出し 火をつける position||`を４つ取り出し、runの中に入れます</br>
`||functions.呼び出し 火をつける position||`の`||functions.position||`をクリックして`||agent.ポイントＡ||`にします</br>
残りも上から`||agent.ポイントＢ||`、`||agent.ポイントＣ||`、`||agent.ポイントＤ||`に変えましょう<br>
```blocks
let ポイントA: Position = null
let ポイントD: Position = null
let ポイントB: Position = null
let ポイントC: Position = null
player.onChat("a", function (x, y, z) {
    ポイントA = world(x, y, z)
})
player.onChat("d", function (x, y, z) {
    ポイントD = world(x, y, z)
})
player.onChat("b", function (x, y, z) {
    ポイントB = world(x, y, z)
})
player.onChat("c", function (x, y, z) {
    ポイントC = world(x, y, z)
})
function 火をつける (座標: Position) {
    blocks.place(FIRE, 座標)
}
player.onChat("run", function () {
    火をつける(ポイントA)
    火をつける(ポイントB)
    火をつける(ポイントC)
    火をつける(ポイントD)
})




```

## Step 10
これで完成です</br>
右下の実行ボタンを押し、チャットコマンドに ポイントAの座標を保存したいときは"a x y z"（x,y,zはポイントの座標） と打ってみましょう</br>
すべてのポイントの座標を保存できたら、金色のスイッチをふんでからチャットコマンドに"run"と入力して火をつけましょう<br>
<img style="width:100%" src="https://i.ibb.co/j8PwRtL/l1-3-2.gif"><br>
