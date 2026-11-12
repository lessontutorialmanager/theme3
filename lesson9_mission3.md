# ランダムにカミナリを落とそう！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            たおした数 = 0
            blocks.fill(
            AIR,
            world(79, 49, 109),
            world(87, 50, 116),
            FillOperation.Replace
            )
            とびらをあける()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            とびら = false
        }
    }
    if (blocks.testForBlock(BEDROCK, pos(0, -1, 0))) {
        if (とびら == false) {
            loops.pause(3000)
            カミナリを落とす()
        }
    }
})
function カミナリを落とす () {
    ランダムな数 = randint(1, 2)
    if (ランダムな数 == 1) {
        for (let index = 0; index < 3; index++) {
            開始位置 = randpos(
            world(79, 48, 109),
            world(87, 48, 117)
            )
            blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
            player.say("カミナリだ！")
            loops.pause(1000)
            mobs.spawn(LIGHTNING_BOLT, 開始位置)
            blocks.place(BEDROCK, 開始位置)
        }
    }
}
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    gameplay.setDifficulty(NORMAL)
}

let たおした数 = 0
let ランダムな数 = 0
let 開始位置: Position = world(0, 0, 0)
let とびら = false
とびら = false



```

```template

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            たおした数 = 0
            blocks.fill(
            AIR,
            world(79, 49, 109),
            world(87, 50, 116),
            FillOperation.Replace
            )
            とびらをあける()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            とびら = false
        }
    }
})
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    gameplay.setDifficulty(NORMAL)
}
let 開始位置: Position = world(0, 0, 0)
let とびら = false
とびら = false

```


## ランダムにカミナリを落とそう！@unplugged
プレイヤーがステージ内にいるときに、一定の確率でランダムな場所にカミナリを落とそう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete3.gif">



## 目標(もくひょう)
ゲームがはじまったときに、ステージの中にカミナリが落ちるようにしよう！
・``||functions.カミナリを落とす||``を作り、``||variables.開始位置||``に**ワールド(79, 48, 109)から(87, 48, 117)の間のランダムな座標**を入れ、カミナリを落とすようにする
・とびらがしまってゲームが始まったら、3秒に1回``||functions.カミナリを落とす||``を呼び出すようにする
※今回のしくみに必要のない部分のプログラムは、表示しないようにしています
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete3.gif">



## カミナリを落とす流れを考える
いきなりカミナリがランダムな場所に落ちてしまうと、プレイヤーはよけることができません・・・
カミナリが落ちる前に、足元のブロックを**黄色の彩釉テラコッタ**に変えて、どこに落ちるかわかるようにしましょう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_thunder.gif">



## 関数を作る
まずは、``||functions.カミナリを落とす||``という関数を作ろう！

```blocks

function カミナリを落とす () {
}

```



## ランダムな場所にカミナリを落とす
カミナリが落ちるながれを、**自分で考えてプログラミング**しよう！
①``||variables.開始位置||``に**ワールド(79, 48, 109)から(87, 48, 117)の間のランダムな座標**を入れる
②``||variables.開始位置||``に入った座標に、**黄色の彩釉テラコッタ**をおいて、「カミナリだ！」とメッセージ送信する
③**1秒(1000ミリ秒)**待った後に、``||variables.開始位置||``に入った座標に、**ライトニングボルト**をスポーンさせる
④``||variables.開始位置||``に入った座標に、**岩盤**をおいて、もとにもどす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_thunder.gif">

```blocks

function カミナリを落とす () {
    開始位置 = randpos(
    world(79, 48, 109),
    world(87, 48, 117)
    )
    blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
    player.say("カミナリだ！")
    loops.pause(1000)
    mobs.spawn(LIGHTNING_BOLT, 開始位置)
    blocks.place(BEDROCK, 開始位置)
}

```



## くりかえしを設定する
カミナリを落とす流れを、**3回くりかえす**ように自分で考えてプログラミングしよう！

```blocks

function カミナリを落とす () {
    for (let index = 0; index < 3; index++) {
        開始位置 = randpos(
        world(79, 48, 109),
        world(87, 48, 117)
        )
        blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
        player.say("カミナリだ！")
        loops.pause(1000)
        mobs.spawn(LIGHTNING_BOLT, 開始位置)
        blocks.place(BEDROCK, 開始位置)
    }
}

```



## ランダムにカミナリを落とすようにする方法
今のままだと、**ずっとカミナリが落ちる**ことになります・・・
くじを引くように、**ランダムなタイミング**でカミナリが落ちるようにしよう！
はじめに``||variables.ランダムな数||``に**1から2の間のランダムな数**を入れて、``||variables.ランダムな数||``**に入った数が1のとき**だけカミナリが落ちるように条件分岐すると、50%のかくりつでカミナリが落ちるようになります
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_random_thunder.png">




## 条件分岐する
先ほど考えたことをもとにして、、ランダムにカミナリが落ちるように、**自分で考えてプログラミング**しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_random_thunder.png">

```blocks

function カミナリを落とす () {
    ランダムな数 = randint(1, 2)
    if (ランダムな数 == 1) {
        for (let index = 0; index < 3; index++) {
            開始位置 = randpos(
            world(79, 48, 109),
            world(87, 48, 117)
            )
            blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
            player.say("カミナリだ！")
            loops.pause(1000)
            mobs.spawn(LIGHTNING_BOLT, 開始位置)
            blocks.place(BEDROCK, 開始位置)
        }
    }
}

```



## 関数を呼び出すときを考える
作ったプログラムをいつ呼び出すか考えよう！
カミナリが、**ゲームの間だけ落ちる**ようにしたいと思います
・**とびらがしまったあと**ゲームが始まる
・ゲームのステージは、**岩盤**でできてい
**プレイヤーが岩盤の上**に立っていて、``||variables.とびら||``が**偽**のときに``||functions.カミナリを落とす||``を呼び出せばよさそうです！



## 関数を呼び出す
**プレイヤーが岩盤の上**に立っていて、``||variables.とびら||``が**偽**のときに``||functions.カミナリを落とす||``を呼び出すよう、**自分で考えてプログラミング**しよう！
・プレイヤーが白色の彩釉テラコッタや黄色の彩釉テラコッタのの上に立っているときのプログラムを参考にしよう！
・すぐに何度も呼び出すと、カミナリが短い間にたくさん落ちてしまうので、**関数を呼び出したあと、3秒(3000ミリ秒)待つ**ようにしよう


```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            たおした数 = 0
            blocks.fill(
            AIR,
            world(79, 49, 109),
            world(87, 50, 116),
            FillOperation.Replace
            )
            とびらをあける()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            とびら = false
        }
    }
    if (blocks.testForBlock(BEDROCK, pos(0, -1, 0))) {
        if (とびら == false) {
            カミナリを落とす()
            loops.pause(3000)
        }
    }
})
function カミナリを落とす () {
    ランダムな数 = randint(1, 2)
    if (ランダムな数 == 1) {
        for (let index = 0; index < 3; index++) {
            開始位置 = randpos(
            world(79, 48, 109),
            world(87, 48, 117)
            )
            blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
            player.say("カミナリだ！")
            loops.pause(1000)
            mobs.spawn(LIGHTNING_BOLT, 開始位置)
            blocks.place(BEDROCK, 開始位置)
        }
    }
}
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    gameplay.setDifficulty(NORMAL)
}

let たおした数 = 0
let ランダムな数 = 0
let 開始位置: Position = world(0, 0, 0)
let とびら = false
とびら = false

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、**白の彩釉テラコッタ**の上に立って中に入り、**橙色の彩釉テラコッタ**の上に立ってとびらをしめよう
ステージの上でしばらく待って、カミナリがランダムな場所に落ちているのを確認したら、おくに進んでテレポートしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete3.gif">
<br></br>
テレポートしたら、**村人に話しかけよう**
