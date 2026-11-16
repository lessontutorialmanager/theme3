# とびらのしくみをつくろう！

```blocks

function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
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
player.onChat("gate", function () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    blocks.place(WHITE_GLAZED_TERRACOTTA, world(83, 48, 105))
    blocks.place(ORANGE_GLAZED_TERRACOTTA, world(83, 48, 107))
})
let とびら = false
とびら = false



```

```template

player.onChat("gate", function () {
})

```


## とびらのしくみをつくろう！ @unplugged
とびらをつくって、あけしめするしくみをつくろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete2.gif">



## 目標(もくひょう)
とびらをつくり、あけしめするしくみをつくろう！
・チャットコマンドで「gate」と入力すると、建物との間に、**空色の色付きガラス**の扉をつくり、その前と後ろに**白色の彩釉テラコッタと橙色の彩釉テラコッタ**をおく
・**白色の彩釉テラコッタ**の上に立つと、とびらがひらいてプレイヤーに**ネザライトの剣と盾(たて)**をわたす
・**橙色の彩釉テラコッタ**の上に立つと、とびらがとじる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete2.gif">



## とびらをつくる
下の図をさんこうにして、チャットコマンドで「set」と入力したときに**空色の色付きガラス**を**絶対座標**でならぶよう、**自分で考えてプログラミング**しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_center.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_side.png">

```blocks

player.onChat("gate", function () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
})

```



## テラコッタをおく
とびらの前とうしろに、とびらのあけしめのスイッチとなる**白色の彩釉テラコッタと橙色の彩釉テラコッタ**をおくよう、**自分で座標を考えてプログラミング**しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_terracotta_center.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_terracotta_side.png">

```blocks

player.onChat("gate", function () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    blocks.place(WHITE_GLAZED_TERRACOTTA, world(83, 48, 105))
    blocks.place(ORANGE_GLAZED_TERRACOTTA, world(83, 48, 107))
})

```



## とびらのしくみを考える
**白色の彩釉テラコッタ**の上に立ったときにとびらがひらき、**橙色の彩釉テラコッタ**の上に立ったときにとびらがしまるようにするしくみを考えよう！
プレイヤーがいつテラコッタの上にのってもプログラムを実行できるように、``||loops.ずっと||``を使って、いつもチェックするのがよさそうです！
``||functions.とびらをあける||``、``||functioins.とびらをしめる||``という関数をつくり、条件分岐で、**プレイヤーの1ブロック下にテラコッタがあるとき**に呼び出すようにしましょう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_conditional1.png">




## 関数をつくる
まずは``||functions.とびらをあける||``、``||functions.とびらをしめる||``をつくろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_make_function1.png">




## ブロックをならべる
``||functions.とびらをあける||``には**空気ブロック**を、``||functions.とびらをしめる||``には**空色の色付きガラス**をならべるように、下の図をさんこうに**自分で考えてプログラミング**しよう
``||player.チャットコマンドgateを入力した時||``のプログラムをヒントにしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_terracotta_center.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_terracotta_side.png">

```blocks

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
}

```



## プレイヤーにアイテムをわたす
``||functions.とびらをあける||``の中に、プレイヤーに**ネザライトの剣**と**盾**を1つずつわたすよう、**自分で考えてプログラミング**しよう
また、**けんとたてをてにいれた！**とメッセージ送信するようにしよう

```blocks

function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}

```



## イベントを検知する①
プレイヤーが**白色の彩釉テラコッタ**の上に立ったのを検知して、``||functions.とびらをあける||``を呼び出すようにしよう！
・``||loops.ループ||``から``||loops.ずっと||``をとりだす
・``||logic.論理||``から``||logic.もし～なら||``をとりだして``||loops.ずっと||``にはめこむ
・``||blocks.ブロック||``から``||blocks.～が(~0, ~0, ~0)に存在する||``をとりだして、条件にはめこむ
・ブロックの種類を**白色の彩釉テラコッタ**にして、座標を**(~0, ~-1, ~0)**にする
・``||functions.関数||``から``||functions.呼び出し とびらをあける||``をとりだしてはめこむ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_event2.gif">



## イベントを検知する②
おなじように、プレイヤーが**橙色の彩釉テラコッタ**の上に立ったのを検知して、``||functions.とびらをしめる||``を呼び出すように**自分で考えてプログラミング**しよう！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        とびらをあける()
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        とびらをしめる()
    }
})
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}

```



## とびらがあいているかたしかめる①
**白色の彩釉テラコッタ**の上にのった時にとびらをあけて、ネザライトの剣と盾をわたすようにプログラミングしました
しかし、今のままだと、**白色の彩釉テラコッタ**の上にいるあいだずっと剣と盾をわたしつづけてしまいます…
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_error2.gif">
``||functions.とびらをあける||``と``||functions.とびらをしめる||``を、テラコッタの上にのったときに**一度だけ**実行するにはどうすればよいでしょうか？
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_check_1.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_check_2.png">



## とびらがあいているかたしかめる②
**白色の彩釉テラコッタ**の上にのっているかどうかにくわえて、**とびらがあいているか**も条件分岐でかくにんすればよさそうです！
とびらをチェックするために、新しく変数``||variables.とびら||``を作って、``||variables.とびら||``が**真**ならあいている、**偽**ならしまっているというふうにしよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_check_3.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_gate_check_4.png">
下の図で、これから作る条件分岐をたしかめましょう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_flow2.png">



## 変数をつくる
新しく変数``||variables.とびら||``をつくろう
はじめ、とびらは**しまっている**はずなので、プログラムを実行したときに``||variables.とびら||``を**偽**にしよう
・変数``||variables.とびら||``をつくる
・``||loops.ループ||``から``||loops.最初だけ||``をとりだし、``||variables.変数 とびら を0にする||``をはめ込む
・``||logic.論理||``から``||logic.偽||``をとりだし、``||variables.変数 とびら を0にする||``にはめ込む
これで、とびらがしまっているということを変数であらわすことができるようになりました！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_make_variable2.gif">



## 条件分岐をついかする①
つくった``||variables.とびら||``をつかって、下の図のようになるように、条件分岐をついかしよう！
・``||logic.もし 白の彩釉テラコッタが(~0, ~-1, ~0)にある なら||``の中に、もうひとつ``||logic.もし～なら||``をいれる
・``||logic.もし とびら = 偽 なら||``となるように条件を入れる
・``||functions.呼び出し とびらをあける||``を、``||logic.もし とびら = 偽 なら||``のなかにうごかす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_flow2.png">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            とびらをあける()
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
            とびらをしめる()
    }
})
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}

```



## 条件分岐をついかする②
おなじように、プレイヤーが**橙色の彩釉テラコッタ**の上に立ったときに、もし``||variables.とびら||``が**真**なら、``||functions.とびらをしめる||``を呼び出すように、**自分で考えて条件分岐をついかしよう！**

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            とびらをあける()
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
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
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「gate」と入力して**空色の色付きガラスのとびら**を並べよう
とびらができたら、**白の彩釉テラコッタ**の上に立って**ネザライトの剣**と**盾**をうけとって中に入り、**橙色の彩釉テラコッタ**の上に立ってとびらをしめよう
とびらがしまったのをかくにんしたら、**おくにすすんで地上にテレポートしよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete2.gif">
<br></br>
テレポートしたら、**村人に話しかけよう**
