# LESSON 1 
```block
function ブロックを壊す (高さ: number) {
    for (let index = 0; index < 高さ; index++) {
        for (let index = 0; index < 8; index++) {
            agent.destroy(FORWARD)
            agent.move(RIGHT, 1)
        }
        agent.move(LEFT, 8)
    }
}
player.onChat("run", function (高さ) {
    agent.teleport(player.position(), positions.toCompassDirection(player.getOrientation()))
    ブロックを壊す(高さ)
})

```

```template
player.onChat("run", function () {
	
})
```

## 変数と関数を使ってプログラミングしてみよう @unplugged
エージェントを操作して入口の砂利を壊そう！<br>
<img style="display: block; margin: auto;" height="40%" width="40%" src="https://i.ibb.co/8cpSW05/l1-1-2.png">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・プレイヤーは必ず矢印ブロックの上に乗ってプログラムを実行する<br>
・チャットで「run ○」と入力したら、エージェント指定した高さだけ砂利を壊すプログラミングをする<br>
・砂利がなくなれば次の砂利の位置に移動してプログラムを実行する<br>
<img style="width:100%" src="https://i.ibb.co/bd395Js/l1-1-9.gif"><br>

## 関数を作ろう
まずは壊す砂利の高さを変えられるように関数を作りましょう<br>
<img style="width:100%" src="https://i.ibb.co/wNrn0K9/l1-1-3.png"><br>

## Step 1
高度なブロックをクリックして、`||functions.関数||`をクリックします</br>
`||functions.関数を作成する…||`をクリックして、【doSomething】を【ブロックを壊す】に入力しなおします</br>
『パラメーターを追加する』の『数値』をクリックして、【数値】を【高さ】に入力しなおしてから完了をクリックします<br>
<img style="width:100%" src="https://i.ibb.co/hLGmbpZ/l1-1-4.gif"><br>

```blocks
function ブロックを壊す (高さ: number) {
	
}
player.onChat("run", function () {
	
})

```

## Step 2
次は関数「ブロックを壊す」の中にエージェントが砂利を壊すプログラムを作ります</br>
`||loops.くりかえし４回||`を取り出して関数の中に入れ、４回を８回に変更します</br>
`||agent.エージェントに前を破壊させる||`と`||エージェントを前に１ブロック移動させる||`を取り出し、`||loops.くりかえし８回||`の中に入れます</br>
`||エージェントを前に１ブロック移動させる||`の前を右に変更しましょう<br>
<img style="width:100%" src="https://i.ibb.co/2dLwHbs/l1-1-5.gif"><br>
<br>
```blocks
function ブロックを壊す (高さ: number) {
    for (let index = 0; index < 8; index++) {
        agent.destroy(FORWARD)
        agent.move(RIGHT, 1)
    }
}
player.onChat("run", function () {
	
})

```

## Step 3
次のブロックを壊す位置にエージェントを移動させて、それを【高さ】の分だけくり返させます</br>
`||エージェントを前に１ブロック移動させる||`を取り出し、`||loops.くりかえし８回||`の下に入れます。そして前を左に変更して、１回を８回に変更しましょう</br>
`||loops.くりかえし４回||`で今まで作成したプログラムをはさみ、`||functions.関数||`の`||variables.高さ||`を４回の部分にドラッグしましょう<br>
<img style="width:100%" src="https://i.ibb.co/BLGmkj8/l1-1-6.gif"><br>
```blocks
function ブロックを壊す (高さ: number) {
    for (let index = 0; index < 高さ; index++) {
        for (let index = 0; index < 8; index++) {
            agent.destroy(FORWARD)
            agent.move(RIGHT, 1)
        }
        agent.move(LEFT, 8)
    }
}
player.onChat("run", function () {
	
})

```

## Step 4
「run ○」（○は高さの数字）と入力した時に関数が実行されるようにしましょう</br>
`||player.チャットコマンドrunを入力した時⊕||`の`||player.⊕||`をクリックします</br>
num1をクリックして変数を作成する…を選んで、【高さ】と入力します</br>
`||functions.関数||`から`||functions.呼び出し ブロックを壊す １||`をrunの中に入れます</br>
`||variables.変数||`から`||variables.高さ||`を`||functions.呼び出し ブロックを壊す １||`の`||functions.１||`に重ねます<br>
<img style="width:100%" src="https://i.ibb.co/7VhrvvS/l1-1-7.gif"><br>
```blocks
function ブロックを壊す (高さ: number) {
    for (let index = 0; index < 高さ; index++) {
        for (let index = 0; index < 8; index++) {
            agent.destroy(FORWARD)
            agent.move(RIGHT, 1)
        }
        agent.move(LEFT, 8)
    }
}
player.onChat("run", function (高さ) {
    ブロックを壊す(高さ)
})


```

## Step 5
最後にエージェントをプレイヤーの場所にテレポートさせましょう<br>
`||agent.エージェントを~0~0~0へ西(xのマイナス方向)向きにテレポートさせる||`を`||functions.呼び出し ブロックを壊す 高さ||`の上に入れます</br>
`||player.プレイヤーの位置||`を`||agent.~0~0~0||`に重ねます</br>
`||positions.ポジション||`から`||positions.0の四方位||`を`||西(xのマイナス方向)||`に重ねます</br>
`||player.プレイヤーの向いている方角||`を`||positions.0の四方位||`に重ねます
<br>
<img style="width:100%" src="https://i.ibb.co/s2dhqQ1/l1-1-8.gif"><br>
```blocks
function ブロックを壊す (高さ: number) {
    for (let index = 0; index < 高さ; index++) {
        for (let index = 0; index < 8; index++) {
            agent.destroy(FORWARD)
            agent.move(RIGHT, 1)
        }
        agent.move(LEFT, 8)
    }
}
player.onChat("run", function (高さ) {
    agent.teleport(player.position(), positions.toCompassDirection(player.getOrientation()))
    ブロックを壊す(高さ)
})


```

## Step 6
これで完成です</br>
右下の実行ボタンを押し、矢印ブロックの上に立ってチャットコマンドに "run ○"（○は砂利の高さ） と打ってみましょう<br>
<img style="width:100%" src="https://i.ibb.co/bd395Js/l1-1-9.gif"><br>
