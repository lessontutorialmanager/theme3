# レースのルールをつくろう！

```blocks

player.onChat("run", function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "よーい・・・", "")
    loops.pause(2000)
    gameplay.title(mobs.target(ALL_PLAYERS), "スタート！", "")
    タイマー = 0
    スイッチ = true
    loops.pause(100)
    player.runChatCommand("jump")
    player.runChatCommand("effect")
    player.runChatCommand("timer")
    player.runChatCommand("goal")
})
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
    }
})
player.onChat("goal", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(BLUE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
            gameplay.title(mobs.target(ALL_PLAYERS), "ゴール！", "" + "きろく　" + タイマー + "びょう")
            タイマー = 0
            スイッチ = false
        }
    }
})
player.onChat("jump", function () {
    while (スイッチ) {
        while (blocks.testForBlock(DIAMOND_BLOCK, pos(0, -1, 0))) {
            mobs.applyEffect(LEVITATION, mobs.target(ALL_ENTITIES), 1, 2)
        }
    }
})
player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
        }
    }
})
function とくしゅこうか () {
    ランダムな数 = randint(1, 4)
    if (ランダムな数 == 1) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 2) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 3) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードダウン・・・")
    } else if (ランダムな数 == 4) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードダウン・・・")
    }
}
player.onChat("make", function () {
    blocks.fill(
    BLUE_GLAZED_TERRACOTTA,
    world(157, 66, -24),
    world(158, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    blocks.blockWithData(OAK_FENCE_GATE, 1),
    world(160, 66, -24),
    world(160, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    STONE_PRESSURE_PLATE,
    world(159, 67, -24),
    world(159, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    GRAY_CARPET,
    world(160, 67, -24),
    world(160, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(160, 69, -25),
    world(160, 69, -19),
    FillOperation.Replace
    )
})
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
スイッチ = false

```

```template

player.onChat("run", function () {
    スイッチ = true
    player.runChatCommand("jump")
    player.runChatCommand("effect")
})
player.onChat("jump", function () {
    while (スイッチ) {
        while (blocks.testForBlock(DIAMOND_BLOCK, pos(0, -1, 0))) {
            mobs.applyEffect(LEVITATION, mobs.target(ALL_ENTITIES), 1, 5)
        }
    }
})
player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
        }
    }
})
function とくしゅこうか () {
    ランダムな数 = randint(1, 4)
    if (ランダムな数 == 1) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 2) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 3) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードダウン・・・")
    } else if (ランダムな数 == 4) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードダウン・・・")
    }
}
player.onChat("make", function () {})
player.onChat("timer", function () {})
player.onChat("goal", function () {})
let ランダムな数 = 0
let スイッチ = false
スイッチ = false


```


## レースのルールをつくろう！@unplugged
ゴールのゲートをつくって、1周のタイムをはかるしくみをつくろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete3.gif">



## 目標(もくひょう)
ゴールのゲートをつくって、1周のタイムをはかるしくみをつくろう！
・チャットで**make**と入力すると、ゴールのゲートがつくられるようにする
・チャットで**run**と入力すると、タイマーがスタートして、ゲームのしくみがスタートするようにする
・ゴールのゲートの**青色の彩釉テラコッタ**の上をとおったとき、タイマーがとまって、ゲームがしゅうりょうするようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete3.gif">



## ゴールのゲートのしくみ
今回は、ゲートにある**青色の彩釉テラコッタ**の上をとおるとゴールとなるようにしようと思います
しかし、ただゲートをつくるだけだと、スタートしてすぐ逆走(ぎゃくそう)することができてしまいます…
そこで、地面に**オークのフェンスゲート**をうめて、となりに**石の感圧版**(かんあつばん)をおくことで、**ただしい向きからのときはゲートがひらいてとおることができ**、**逆走するとゲートがとじているのでとおれない**というしくみをつくりましょう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_how_gate_works.gif">



## ゲートをつくる①
**青色の彩釉テラコッタ**と**オークのフェンスゲート**が下の図のようにならぶように、**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドrunを入力したとき||``のなかにプログラミングをつくる
・オークのフェンスゲートは、図のような向きでならべるために、``||blocks.ブロック||``にある``||blocks.～グループの0番のブロック||``をつかって、``||blocks.フェンスゲートグループの1番のブロック||``となるようにする
・**絶対座標**``||positions.ワールド(0, 0, 0)||``をつかうことをわすれないようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_top_1.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_side_1.png">

```blocks

player.onChat("make", function () {
    blocks.fill(
    BLUE_GLAZED_TERRACOTTA,
    world(157, 66, -24),
    world(158, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    blocks.blockWithData(OAK_FENCE_GATE, 1),
    world(160, 66, -24),
    world(160, 66, -20),
    FillOperation.Replace
    )
})

```



## ゲートをつくる②
つぎに、**石の感圧版**と**灰色のカーペット**が下の図のようにならぶように、**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドrunを入力したとき||``のなかにプログラミングをつくる
・**絶対座標**``||positions.ワールド(0, 0, 0)||``をつかうことをわすれないようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_top_2.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_side_2.png">

```blocks

player.onChat("make", function () {
    blocks.fill(
    BLUE_GLAZED_TERRACOTTA,
    world(157, 66, -24),
    world(158, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    blocks.blockWithData(OAK_FENCE_GATE, 1),
    world(160, 66, -24),
    world(160, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    STONE_PRESSURE_PLATE,
    world(159, 67, -24),
    world(159, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    GRAY_CARPET,
    world(160, 67, -24),
    world(160, 67, -20),
    FillOperation.Replace
    )
})

```



## ゲートをつくる③
さいごに、**空色のステンドグラス**が下の図のようにならぶように、**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドrunを入力したとき||``のなかにプログラミングをつくる
・**絶対座標**``||positions.ワールド(0, 0, 0)||``をつかうことをわすれないようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_gate.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_top_3.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_from_side_3.png">

```blocks

player.onChat("make", function () {
    blocks.fill(
    BLUE_GLAZED_TERRACOTTA,
    world(157, 66, -24),
    world(158, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    blocks.blockWithData(OAK_FENCE_GATE, 1),
    world(160, 66, -24),
    world(160, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    STONE_PRESSURE_PLATE,
    world(159, 67, -24),
    world(159, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    GRAY_CARPET,
    world(160, 67, -24),
    world(160, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(160, 69, -25),
    world(160, 69, -19),
    FillOperation.Replace
    )
})

```



## タイマーのしくみを考える
つぎに、1周にかかった時間をはかるためのタイマーのしくみをかんがえよう！
・``||variables.スイッチ||``が**真**のときにくりかえすようにする
・1秒(1000ミリ秒)まつ⇒``||variables.タイマー||``の数字を1ふやす
・とすれば、``||variables.タイマー||``の中に、``||variables.スイッチ||``が真のあいだにかかった時間が入りそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow_timer.png">



## タイマーをつくる
さきほどのかんがえをもとにして、``||player.チャットコマンドtimerを入力した時||``の中に、**自分で考えてプログラミング**しよう！
・変数``||variables.タイマー||``をつくる
・``||variables.スイッチ||``が**真**のときにくりかえすようにする
・1秒(1000ミリ秒)まつ⇒``||variables.タイマー||``の数字を1ふやす
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow_timer.png">

```blocks

player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
    }
})
let タイマー = 0
let スイッチ = false

```



## ゴールしたときのことをかんがえる
ゴールしたときに、何をすればよいかかんがえよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_goal.gif">
・**青色の彩釉テラコッタ**の上をとおったときに実行する
・「ゴール！きろく　○びょう」とタイトルを表示する
・ゲームを終了するために、``||variables.スイッチ||``を**偽**にして、つぎのレースのために``||variables.タイマー||``を0にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow_goal.png">



## ゴールしたときのプログラムをつくる
さきほどのかんがえをもとにして、``||player.チャットコマンドgoalを入力した時||``の中に、**自分で考えてプログラミング**しよう！
・``||variables.スイッチ||``が**真**のとき、くりかえすようにする
・**青色の彩釉テラコッタ**の上をとおったときに実行するよう、**条件分岐**をつくる
・タイトルは、サブタイトルに``||text.文字列をつなげる||``と``||variables.タイマー||``をつかって「きろく　○びょう」と表示できるようにする
・ゲームを終了するために、``||variables.スイッチ||``を**偽**にして、つぎのレースのために``||variables.タイマー||``を0にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_title.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow_goal.png">

```blocks

player.onChat("goal", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(BLUE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
            gameplay.title(mobs.target(ALL_PLAYERS), "ゴール！", "" + "きろく　" + タイマー + "びょう")
            タイマー = 0
            スイッチ = false
        }
    }
})
let タイマー = 0
let スイッチ = false

```



## チャットでrunと入力したとき
さいごに、前回のミッションでつくった``||player.チャットコマンドrunを入力した時||``に、プログラムをついかしよう！
・``||variables.スイッチ||``を真にする**前**に、「よーい・・・　スタート！」とタイトルを表示して、``||variables.タイマー||``を0にする
・あたらしくつくったチャットコマンド**timer**と**goal**を実行するようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow_run.png">



## タイトルを表示する
チャットで**run**と入力した時に、「よーい・・・　スタート！」とタイトルを表示するようにしよう！
・タイトル「よーい・・・」を表示したあと、**2秒(2000ミリ秒)**まって「スタート！」と表示する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_start.gif">



## チャットコマンドを実行する
あたらしくつくったチャットコマンド**timer**と**goal**を実行するようにしよう！
また、早く実行されすぎないように、4つのチャットコマンドjump、effect、timer、goalを実行する**前**に、``||loops.100ミリ秒まつ||``をいれよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_start.gif">

```blocks

player.onChat("run", function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "よーい・・・", "")
    loops.pause(2000)
    gameplay.title(mobs.target(ALL_PLAYERS), "スタート！", "")
    タイマー = 0
    スイッチ = true
    loops.pause(100)
    player.runChatCommand("jump")
    player.runChatCommand("effect")
    player.runChatCommand("timer")
    player.runChatCommand("goal")
})
let タイマー = 0
let スイッチ = false

```

## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで**make**と入力して、ゴールのゲートをつくろう
ゲートができあがったら、チャットで**run**と入力してレースをスタートし、**ゴールするまで1周してみよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete3.gif">
<br></br>
1周したら、**村人に話しかけよう**
