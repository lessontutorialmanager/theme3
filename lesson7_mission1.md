# LESSON 1 
```block
player.onChat("build", function (一辺の長さ, 繰り返す回数) {
    for (let index = 0; index < 繰り返す回数; index++) {
        一辺を置く(一辺の長さ)
        agent.turn(RIGHT_TURN)
    }
})
function 一辺を置く(長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}
```

```template
player.onChat("build", function() {

})
```

## 関数を使っていろいろなプログラムを書こう @unplugged
エージェントを操作して螺旋階段を作ろう！<br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://i.ibb.co/j5R77pS/3rd-7-1.gif">


## Step 1
まず、プログラムの仕様を確認しましょう。<br>
今回は、正方形のスペースに螺旋階段を作ります。螺旋階段は、正方形の四隅の部分がクォーツブロックになっていて、その間をクォーツの階段ブロックでつないでいきます。では、どのようにおいていけばよいでしょうか。
<br>

## Step 2
正方形は、(一辺の長さ - 1)の長さを持つ棒が 4 つ集まったものと考えることができます。ですから、ブロックを(一辺の長さ - 1)個だけ置く関数を作れば、エージェントの向きを変えながら 4 回繰り返すことで正方形を作ることができます。
<br>

## Step 3 
螺旋階段の場合は、「階段ブロックを置いた時には y 座標(高さ)が 1 大きくなり」、「クォーツブロックを置いた時には高さが変わらない」というような変更を行えばよいです。また、高さが変わるので、関数を繰り返す回数によって好きな長さの階段を作ることができます。何回繰り返せばよいかは、実行するときに考えることにします。
<br>

## Step 4
まず、正方形の一辺に当たる部分に階段とクォーツブロックを設置するという部分を、関数にしておきます。
`||function.関数を作成する||`をクリックし、名前を「一辺を置く」にします。また、引数として「数値」をクリックし、その名前を「長さ」にします。<br>
<br>

```blocks
function 一辺を置く (長さ: number) {
	
}
```

## Step 5 
まず、階段ブロックを置いてもらいます。正方形の一辺のうち、端の部分は階段ではなくクォーツブロックですから、階段ブロックを置く回数は(長さ - 2)回です。<br>
ですから、`||loops.くりかえし 4 回||`を取り出して関数の中に入れ、さらに`||math.0 - 0||`を取り出し、`||loops.4||`の部分にあてはめ、(長さ - 2)回に変更します。
<br>

```blocks
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
    	
    }
}
```

## Step 6
エージェントに「クォーツの階段ブロック」を 1 個持たせます。`||agent.エージェントに [ブロック] を 1 個、自分のスロット 1 番に設定させる||`を使いましょう。
<br>

```blocks
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
    }
}

```

## Step 7
はじめ、エージェントの足元にはブロックがあるので、階段状になるように自分の前に階段ブロックを置けばよい、ということになります。<br>
置いた後は上へ 1 ブロック、前へ 1 ブロック移動して次の階段ブロックを置く準備をしましょう。<br>
※前にブロックを置いたので、上へ移動するよりも先に前へ移動することはできないことに注意しましょう。
<br>

```blocks
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
}
```

## Step 8
階段ブロックを置いた後は、正方形の四隅に当たる場所にクォーツブロックを置いていきます。まずはエージェントにブロックを持たせましょう。<br>
このブロックは一辺の長さにかかわらず 1 個だけ置くので、繰り返しの外側に`||agent.エージェントに [ブロック] を 1 個、自分のスロット 1 番に設定させる||`をあてはめます。
<br>

```blocks
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
}
```

## Step 9
紙にエージェントの位置を書き込むなどして、クォーツブロックを置くには「どこへ移動して」「どの方向に置けばよい」か自分で考えてみましょう。
<br>

```blocks
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}
```

## Step 10
これで一辺の長さの階段を作ることができました。あとはエージェントの向きを変えながら適切な回数繰り返せばよいです。<br>
`||player.チャットコマンド "build" を入力した時||`の + を 2 回押し、パラメータ「一辺の長さ」「繰り返す回数」を追加しましょう。
<br>

```blocks
player.onChat("build", function (一辺の長さ, 繰り返す回数) {
	
})
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}
```

## Step 11
`||player.チャットコマンド "build" を入力した時||`の中では、関数`||function.一辺を置く||`を`||variables.繰り返す回数||`だけ繰り返すことになります。<br>
`||player.チャットコマンド "build" を入力した時||`の中に`||loops.くりかえし 4 回||`を入れ、`||variables.繰り返す回数||`を`||loops.4||`の部分にあてはめます。そして、その中で`||function.一辺を置く||`を呼び出しましょう。引数は`||variables.一辺の長さ||`です。
<br>

```blocks
player.onChat("build", function (一辺の長さ, 繰り返す回数) {
    for (let index = 0; index < 繰り返す回数; index++) {
        一辺を置く(一辺の長さ)
    }
})
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

```

## Step 12
ブロックを一辺置いた後は、エージェントの向きを右に変えることになります。関数の呼び出しの後でエージェントの向きを右に変えましょう。
<br>

```blocks
player.onChat("build", function (一辺の長さ, 繰り返す回数) {
    for (let index = 0; index < 繰り返す回数; index++) {
        一辺を置く(一辺の長さ)
        agent.turn(RIGHT_TURN)
    }
})
function 一辺を置く (長さ: number) {
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
        agent.move(FORWARD, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.move(FORWARD, 1)
    agent.place(DOWN)
}

```

## Step 13
これでプログラムは完成です。最後にパラメータについて考えましょう。<br>
まず、今回の塔は一辺の長さが 4 です。このとき、一辺につき高さは階段ブロックの数だけ上がるので、 2 だけ上昇します。塔の高さは 10 になっているので、繰り返す回数は 5 となります。<br>
チャットコマンドで、"build 4 5"と打って実行してみましょう。
<br>