# コースをならべよう！

```blocks

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
player.onItemInteracted(STICK, function () {
    はんいのはじまり = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    player.say("はんいのはじまり　" + はんいのはじまり)
})
player.onItemInteracted(BLAZE_ROD, function () {
    はんいのおわり = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    player.say("はんいのおわり　" + はんいのおわり)
})
player.onChat("run", function () {
    blocks.fill(
    GRAY_CONCRETE,
    はんいのはじまり,
    はんいのおわり,
    FillOperation.Replace
    )
})
let はんいのはじまり: Position = null
let はんいのおわり: Position = null

```

```template

player.onChat("run", function () {})

```


## コースをならべよう！ @unplugged
カートがはしるためのコースをならべよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete1.gif">



## 目標(もくひょう)
カートではしるためのコースをつくろう！
・プレイヤーに、**棒**と**ブレイズロッド**をわたす
・棒をつかったとき、**プレイヤーがいる場所のあしもとの座標**を変数``||variables.はんいのはじまり||``にいれ、**メッセージ送信**する
・ブレイズロッドをつかったとき、**プレイヤーがいる場所のあしもとの座標**を変数``||variables.はんいのおわり||``にいれ、**メッセージ送信**する
・チャットでrunと入力すると、``||variables.はんいのはじまり||``から``||variables.はんいのおわり||``まで、**灰色のコンクリートブロック**がならぶようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete1.gif">



## プレイヤーにアイテムをわたす
プログラムを実行したときに、プレイヤーに**棒**と**ブレイズロッド**をわたすよう、**自分で考えてプログラミング**しよう！



## 変数を作る
変数``||variables.はんいのはじまり||``と``||variables.はんいのおわり||``を作ろう！




## アイテムを使ったとき
プレイヤーが**棒**、**ブレイズロッド**を使ったときにすることを、下をヒントにしながら**自分で考えてプログラミング**しよう！
・**棒**を使ったとき：``||variables.はんいのはじまり||``に、**プレイヤーの1ブロック下の座標**を入れ、「はんいのはじまり：○」となるように**メッセージ送信**する
・**ブレイズロッド**を使ったとき：``||variables.はんいのおわり||``に、**プレイヤーの1ブロック下の座標**を入れ、「はんいのおわり：○」となるように**メッセージ送信**する
・プレイヤーの1ブロック下の座標を入れるには、``||positions.(0, 0, 0) + (0, 0, 0)||``と``||player.プレイヤーの位置||``をくみあわせる
・「はんいのはじまり：○」のように、変数に入れた座標を表示するには、``||text.文字列をつなげる||``と**変数**をくみあわせる



## チャットを入力したとき
チャットで**run**と入力したときに、``||variables.はんいのはじまり||``から``||variables.はんいのおわり||``まで、**灰色のコンクリートブロック**をならべるように、**自分で考えてプログラミング**しよう！



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、コースの中に入って、**灰色のコンクリートブロック**をならべていこう！
ヒントとして、コース上に目印があります！
下の目印の場所では、**棒**を使おう
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_start_position.png">
下の目印の場所では、**エンドロッド**を使おう
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_end_position.png">
ブロックをならべるはんいが決まったら、チャットで**run**と入力しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson10/L10_complete1.gif">
<br></br>
これをくりかえして、コース全体に灰色のコンクリートブロックをならべたら、**村人に話しかけよう**

```blocks

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
player.onItemInteracted(STICK, function () {
    はんいのはじまり = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    player.say("はんいのはじまり　" + はんいのはじまり)
})
player.onItemInteracted(BLAZE_ROD, function () {
    はんいのおわり = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    player.say("はんいのおわり　" + はんいのおわり)
})
player.onChat("run", function () {
    blocks.fill(
    GRAY_CONCRETE,
    はんいのはじまり,
    はんいのおわり,
    FillOperation.Replace
    )
})
let はんいのはじまり: Position = null
let はんいのおわり: Position = null

```
