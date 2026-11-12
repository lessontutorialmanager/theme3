# レースを面白くするしくみをつくろう！

```blocks

player.onItemInteracted(STICK, function () {
    blocks.place(DIAMOND_BLOCK, pos(0, -1, 0))
})
player.onItemInteracted(BLAZE_ROD, function () {
    blocks.place(REDSTONE_BLOCK, pos(0, -1, 0))
})
player.onChat("run", function () {
    スイッチ = true
    player.runChatCommand("jump")
    player.runChatCommand("effect")
})
player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
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
let ランダムな数 = 0
let スイッチ = false
スイッチ = false
mobs.give(
mobs.target(LOCAL_PLAYER),
STICK,
1
)
mobs.give(
mobs.target(LOCAL_PLAYER),
BLAZE_ROD,
1
)

```

```template

mobs.give(
mobs.target(LOCAL_PLAYER),
STICK,
1
)
mobs.give(
mobs.target(LOCAL_PLAYER),
BLAZE_ROD,
1
)
player.onChat("effect", function () {})
player.onChat("run", function () {})
player.onChat("jump", function () {})

```


## レースをおもしろくしよう！ @unplugged
上をとおったらスピードアップしたりおそくなったりするしくみや、川をとびこえるしくみをつくろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete2.gif">



## 目標(もくひょう)
上をとおったらスピードアップしたりおそくなったりするしくみや、川をとびこえるしくみをつくろう！
・**棒**をつかったときに**プレイヤーの足元**に**ダイヤモンドのブロック**を、**エンドロッド**をつかったときに**プレイヤーの足元**に**レッドストーンブロック**をおくようにする
・レッドストーンの上をとおったら、ランダムにスピードが上がったり下がったりするようにする
・ダイヤモンドのブロックの上をとおったら、プレイヤーとレーシングカートがうかぶようにする
それぞれ、どうすればできそうかかんがえよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete2.gif">



## レッドストーンの上をとおったとき
プレイヤーがレッドストーンの上をとおったときに、ランダムでスピードをかえるにはどうすればよいかかんがえてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_change_speed.gif">
<br></br>
①関数``||functions.とくしゅこうか||``という関数をつくり、プレイヤーにランダムに特殊効果を与えるようにする
②プレイヤーの足元にレッドストーンブロックがあるとき、関数``||functions.とくしゅこうか||``を呼び出す
とすればよさそうです！



## 関数を作る
まずは準備として、``||functions.とくしゅこうか||``と、ランダムな数を入れるための変数``||variables.ランダムな数||``を作成しよう！



## 条件分岐を考える
``||variables.ランダムな数||``に**1～4のランダムな数**を入れ、その数によってランダムな特殊効果を与える条件分岐を、**自分で考えてプログラミング**しよう！
・``||variables.ランダムな数||``が**1**: プレイヤーに**持続時間2**、**効果レベル3**の**移動速度上昇**を与え、「スピードアップ！」と**メッセージ送信**
・``||variables.ランダムな数||``が**2**: プレイヤーに**持続時間2**、**効果レベル5**の**移動速度上昇**を与え、「スピードアップ！」と**メッセージ送信**
・``||variables.ランダムな数||``が**3**: プレイヤーに**持続時間2**、**効果レベル3**の**移動速度低下**を与え、「スピードダウン・・・」と**メッセージ送信**
・``||variables.ランダムな数||``が**4**: プレイヤーに**持続時間2**、**効果レベル5**の**移動速度低下**を与え、「スピードダウン・・・」と**メッセージ送信**
・条件分岐の最後が「でなければ」になっているときは、⊕をおしたあとに⊖をおすと、「でなければもし」に変わります！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_elseif.gif">





## プレイヤーの足元にレッドストーンブロックがあるとき
``||player.チャットコマンドeffectを入力した時||``の中に、プレイヤーの足元に**レッドストーンブロック**があるとき、関数``||functions.とくしゅこうか||``を呼び出すように、**自分で考えてプログラミング**しよう！
・``||blocks.～が(~0, ~0, ~0)に存在する||``と条件分岐をうまくくみあわせよう

```blocks
player.onChat("effect", function () {
    if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
        とくしゅこうか()
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
let ランダムな数 = 0
```



## ダイヤモンドのブロックの上をとおったとき
プレイヤーがダイヤモンドのブロックの上をとおったときに、プレイヤーとレーシングカートがうかぶようにするには、どうすればよいかかんがえてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_levitation.gif">
<br></br>
・プレイヤーの足元にダイヤモンドのブロックがあるとき、プレイヤーに浮遊(ふゆう)の特殊効果を与える
とすればよさそうです！




## プログラムを作る
``||player.チャットコマンドjumpを入力した時||``の中に、プレイヤーが**ダイヤモンドのブロック**の上をとおったときに、プレイヤーとレーシングカートがうかぶように、**自分で考えてプログラミング**しよう
・``||blocks.～が(~0, ~0, ~0)に存在する||``と条件分岐をうまくくみあわせよう
・**持続時間1**、**効果レベル2**の**浮遊**を与えるようにしよう
・プレイヤーだけでなく、レーシングカートもうかぶように、特殊効果を与える相手を、**全てのエンティティ(@e)**にしよう

```blocks

player.onChat("jump", function () {
    while (blocks.testForBlock(DIAMOND_BLOCK, pos(0, -1, 0))) {
        mobs.applyEffect(LEVITATION, mobs.target(ALL_ENTITIES), 1, 2)
    }
})

```



## 特殊効果がうごくようにするしくみをかんがえる
作ったスピードが変わるしくみと、うかぶようになるしくみを、スタートさせるしくみを考えよう！
今回は、チャットでrunと入力したときに、仕組みがうごくようにしよう
ゲームが始まったら、プレイヤーがレッドストーンブロックやダイヤモンドのブロックの上をとおったかどうか、**ずっとかくにんするひつようがあります**
変数``||variables.スイッチ||``が**真**のときはずっとかくにんするようにしよう！
変数``||variables.スイッチ||``が**真**のときはずっとかくにんするようにしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_flow.png">
・変数``||variables.スイッチ||``を作って、チャットでrunと入力したとき**真**にする
・つくったプログラムに、**スイッチが真ならくりかえす**プログラムを追加する
とすればよさそうです！




## 変数を作る
じゅんびとして、変数``||variables.スイッチ||``を作ろう！
・``||variables.変数 スイッチ を0にする||``と、``||logics.偽||``を組み合わせて、プログラムを実行したときは**偽**になるようにする

```blocks

let スイッチ = false
スイッチ = false
mobs.give(
mobs.target(LOCAL_PLAYER),
STICK,
1
)
mobs.give(
mobs.target(LOCAL_PLAYER),
BLAZE_ROD,
1
)

```



## チャットでrunと入力したとき
チャットでrunと入力したときに、変数``||variables.スイッチ||``を**真**に切り替えて、チャットコマンド**jump**、**effect**を実行するように、**自分で考えてプログラミング**しよう！
・チャットコマンドを実行するには、``||player.プレイヤー||``にある、``||player.チャットコマンド～を実行する||``を使う

```blocks

player.onChat("run", function () {
    スイッチ = true
    player.runChatCommand("jump")
    player.runChatCommand("effect")
})

```



## ループを追加する
チャットコマンドjump、effectの中のプログラムが、スイッチが**真**ならくりかえすように、**自分で考えてプログラミング**しよう！
・``||loops.ループ||``の``||loops.もし～ならくりかえし||``をつかう

```blocks

player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
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
let ランダムな数 = 0
let スイッチ = false

```



## レッドストーンブロック、ダイヤモンドのブロックをおけるようにする
最後に、**ダイヤモンドのブロック**、**レッドストーンブロック**をプレイヤーの足元におけるように、**自分で考えてプログラミング**しよう！
・**棒**をつかったとき：**ダイヤモンドのブロック**をプレイヤーの足元におく
・**エンドロッド**をつかったとき：**レッドストーンブロック**をプレイヤーの足元におく

```blocks

player.onItemInteracted(STICK, function () {
    blocks.place(DIAMOND_BLOCK, pos(0, -1, 0))
})
player.onItemInteracted(BLAZE_ROD, function () {
    blocks.place(REDSTONE_BLOCK, pos(0, -1, 0))
})

```


## 実行したらやること
これで、プログラミングはできあがりました！これからすることを、プログラムを実行する前にかくにんしよう！
①コースの中の、**すきな場所**で**エンドロッド**をつかって、**レッドストーンブロック**をおく
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_set_red_stone.gif">
<br></br>
②コースの中の、**しるしがついた場所**で**棒**をつかって、**ダイヤモンドのブロック**をおく
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_set_diamond.gif">
<br></br>
③チャットでrunと入力して、コースを走ってみて、
・レッドストーンブロックの上をとおったらスピードがかわる
・ダイヤモンドのブロックの上をはしったら、うかびあがって川のむこうに行ける
ことをかくにんする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete2.gif">


## 実行しよう！
やることがわかったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
コースのしくみを作って、はしって確認したら、**村人に話しかけよう**
