# LESSON 3
```block
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (agent.inspect(AgentInspection.Block, DOWN) == STONE_BUTTON) {
                agent.interact(DOWN)
            }
            agent.move(FORWARD, 1)
        }
        agent.move(RIGHT, 1)
        agent.move(BACK, 7)
    }
})

```

```template
player.onChat("run", function () {
	
})
```

## 入れ子ループと条件分岐を組み合わせてプログラミングしてみよう @unplugged
エージェントを操作して、石のボタンだけを押していこう！<br>
<img style="display: block; margin: auto;" height="40%" width="40%" src="https://i.ibb.co/JQGyVQV/3rd-3-3.png">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・チャットで「run」と入力したら、エージェントが下にある物を判定して動くプログラミングをする<br>
・エージェントの下に石のボタンがあるなら、ボタンを押す<br>
・エージェントの下に石ボタンがないなら、前にすすむ<br>
<img style="width:100%" src="https://i.ibb.co/MGHH1rx/3rd-l3-q3-2.png"><br>

## ループと条件分岐を組み合わせよう
ループと条件分岐の入れ子を使ってエージェントにボタンを押させよう<br>
<img style="width:100%" src="https://i.ibb.co/hYzzb7W/3rd-l3-q3-2.gif"><br>

## Step 1
まず、エージェントは8×8の床の上を移動するので、`||loops.くりかえし 8 回||`を**2つ**取り出し、入れ子になるようにしましょう。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
        	
        }
    }
})

```

## Step 2
内側のループの中では、エージェントから見て前後の列についてどのような処理をするかを考えます。
<br>
最初に、エージェントがいるマスのボタンが木のボタンか石のボタンかを確認する必要があります。<br>
`||logic.論理||`から`||logic.もし 真 なら ～||`を取り出して内側のループの中に入れます。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (true) {
            	
            }
        }
    }
})

```

## Step 3
ブロックを比べるので、`||logic.論理||`から`||logic.0 = 0||`を取り出して[真]の部分に入れます。<br>
左側の0には`||agent.エージェントの 下 のブロック||`を、右側の0には`||blocks.草ブロック||`をそれぞれ当てはめ、
[草ブロック]を[石のボタン]に変更します。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (agent.inspect(AgentInspection.Block, DOWN) == STONE_BUTTON) {
            	
            }
        }
    }
})

```

## Step 4
石のボタンであった場合にはそのボタンを押すので、`||agent.エージェントを 下 に向けてインタラクトさせる||`を使います。<br>
木のボタンであった場合には何もしません。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (agent.inspect(AgentInspection.Block, DOWN) == STONE_BUTTON) {
                agent.interact(DOWN)
            }
        }
    }
})

```

## Step 5
ボタンを押しても押さなくても、エージェントは前に進んで次のマスのボタンを確認します。<br>
`||agent.エージェントを 前 に 1 ブロック移動させる||`を条件分岐の外に置きましょう。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (agent.inspect(AgentInspection.Block, DOWN) == STONE_BUTTON) {
                agent.interact(DOWN)
            }
            agent.move(FORWARD, 1)
        }
    }
})

```

## Step 6
内側の`||loops.くりかえし 8 回||`によって、エージェントは前後の1列のボタンをすべて確認します。
<br>

## Step 7
2つのループの間では、1列目の確認が終わった後、2列目の最初の位置に移動することを考えます。<br>
(入口のしかけを解いた時のことを思い出してください)
<br>

## Step 8
1列目の確認が終わった位置から2列目の初めの位置に移動するには、「右に1ブロック、後ろに7ブロック」移動すればよいです。
<br>
`||agent.エージェントを 右 に 1 ブロック移動させる||`と`||agent.エージェントを 後ろ に 7 ブロック移動させる||`を使いましょう。
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        for (let index = 0; index < 8; index++) {
            if (agent.inspect(AgentInspection.Block, DOWN) == STONE_BUTTON) {
                agent.interact(DOWN)
            }
            agent.move(FORWARD, 1)
        }
        agent.move(RIGHT, 1)
        agent.move(BACK, 7)
    }
})

```

## Step 9
これで完成です。右下の実行ボタンを押し、チャットコマンドに "run" と打ってみましょう。
