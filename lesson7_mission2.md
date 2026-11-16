# LESSON 2 
```block
player.onChat("build", function (一辺の長さ, 繰り返す回数) {
    for (let index = 0; index < 繰り返す回数; index++) {
        一辺を置く(一辺の長さ)
        agent.turn(RIGHT_TURN)
    }
})
function 一辺を置く (長さ: number) {
    agent.move(BACK, 1)
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(DOWN)
        agent.move(BACK, 1)
        agent.move(DOWN, 1)
    }
    agent.setItem(BLOCK_OF_QUARTZ, 1, 1)
    agent.place(DOWN)
}
```

```template
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

## 作ったプログラムを改造してみよう @unplugged
先ほどのプログラムを改造し、下りの階段が作れるように変更しよう！<br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://i.ibb.co/t4vByLY/3rd-7-2.png">

## Step 1
先ほど作った「螺旋階段を作る」プログラムを少し改造して、下りの階段を作れるようにします。どこをどう変えればよいか、自分で考えてみましょう。<br>
なお、エージェントは最初後ろを向いています。<br>

## Hint 1
階段ブロックの向きはエージェントの向きによって決まるので、エージェントは後ろ向きに進む必要があります。<br>

## Hint 2
まずは 1 つ目の階段ブロックを置くことを考えましょう。<br>
あらかじめ置かれているクォーツブロックと同じ高さに置くので、 1 ブロック後ろに下がり、下に置かせます。<br>

## Hint 3
その後は1ブロック後ろ、1ブロック下に移動し、下に置かせることを繰り返せばよいです。<br>
また、ここから、Hint 2で使った`||agent.1 ブロック後ろに移動する||`は`||loops.くりかえし||`の外側に置く必要があることがわかります。<br>
```blocks
function 一辺を置く (長さ: number) {
    agent.move(BACK, 1)
    for (let index = 0; index < 長さ - 2; index++) {
        agent.setItem(QUARTZ_STAIRS, 1, 1)
        agent.place(DOWN)
        agent.move(BACK, 1)
        agent.move(DOWN, 1)
    }
}
```

## Hint 4
くりかえしが終わった段階でのエージェントの位置を元に、踊り場となるクォーツブロックを置くにはどのようにエージェントを動かせばよいかを考えましょう。<br>

## Hint 5
最後に、`||function.一辺を置く||`が終わった後で、エージェントがどちらに向きを変えればよいかを考えましょう。<br>

## Step 2
完成しましたか？<br>
どうやら下の地面までの高さは **33 ブロック**あるようです。螺旋階段の一辺の長さを **5** として、必要な回数だけ関数を繰り返しましょう。
チャットコマンドを開いて、"build 5 (繰り返す回数) "を入力します。 
<br>
