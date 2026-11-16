# 海の中への道を作ろう！

```blocks

let 開始位置: Position = null
let _3でわったあまり = 0
player.onChat("set", function () {
    開始位置 = world(83, 62, 91)
    while (blocks.testForBlock(WATER, 開始位置)) {
        みちをつくる(開始位置)
        開始位置 = positions.add(
        開始位置,
        pos(0, -1, 1)
        )
    }
})
function みちをつくる (開始位置: Position) {
    _3でわったあまり = 開始位置.getValue(Axis.Z) % 3
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
    if (_3でわったあまり == 0) {
        blocks.place(SEA_LANTERN, 開始位置)
    }
}


```

```template

player.onChat("set", function () {

})

```

## 海の中への道を作ろう！ @unplugged
関数をくりかえし呼び出して、海の中への道を作ろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete1.gif">



## 目標(もくひょう)
``||functions.みちをつくる||``をくりかえし呼び出して、海の中への道を作ろう！
・チャットコマンドで「set」と入力すると、下の建物までくりかえし``||functions.みちをつくる||``を呼び出し、道を作る
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete1.gif">



## 道の作り方
道を作る手順(てじゅん)をかんがえよう！
①``||variables.開始位置||``という変数に、作り始める位置の座標を入れる
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_start_position.png">
②``||functions.みちをつくる||``を呼び出して、``||variables.開始位置||``を基準にして1ブロック分並べる
③``||variables.開始位置||``を次の位置に動かす
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_loop.gif">
これを、建物につながるまでくりかえせば道ができそうです！



## 変数を作る
座標を入れる変数``||variables.開始位置||``を作成しよう！
・``||variables.変数||``を開いて、``||varibales.開始位置||``を作成する！
・``||player.チャットコマンドsetを入力したとき||``を実行したときに、``||variables.開始位置||``に、下の図の矢印の位置の**絶対座標**を**自分で確認して入れる**
※``||positions.ワールド(0, 0, 0)||``を使うことをわすれないようにしよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_start_position.png">

```blocks

player.onChat("set", function () {
    開始位置 = world(83, 62, 91)
})

```



## 関数を作る
みちをつくる関数を用意しよう！
・``||functions.関数||``を開き、**関数を作成する**をおす
・ブロックの種類(しゅるい)を**ガラス**にする
・関数の名前を**みちをつくる**と入力する
・**Position**をおして、座標の引数**開始位置**を作る
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_make_function1.gif">



## ブロックをならべる
``||variables.開始位置||``を基準に、ブロックを並べよう！
・ガラスが下の図のようにならぶように、**自分で考えてプログラミング**しよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_path_center.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_path_side.png">

```blocks

function みちをつくる (開始位置: Position) {
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
}

```



## あかりをつける
このままだとみちの中が暗いので、**3ブロックに1つ**、ゆかに**シーランタン**をおくようにしよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_mod3_none.png">



## 3ブロックに1回シーランタンを置く考え方①
○回に1回何かを実行したいとき、プログラミングではよく**わり算のあまりを使った条件分岐**を使います！
たとえば、下の図を見ると、**Z座標を3でわったあまり**が**1、2、0、1、2、0、…とくりかえしている**ことがわかります
この性質を使って、**Z座標を3でわったあまりが0のときにシーランタンを置く**ようにすれば3回に1回置くことができそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_mod3.png">



## 3ブロックに1回シーランタンを置く考え方②
やることを確認しましょう！
・``||variables.3でわったあまり||``という変数を作り、引数**開始位置**のZ座標(南北)の数字を3でわったあまりを入れる
・``||functions.みちをつくる||``に、条件分岐で``||variables.3でわったあまり||``が**0のときにシーランタンを置く**プログラムを追加
の2つをすれば良さそうです！



## 変数を作る
``||variables.3でわったあまり||``という変数を作り、引数**開始位置**のZ座標(南北)の数字を3でわったあまりを入れよう！
・``||variables.3でわったあまり||``という変数を作る
・``||functions.みちをつくる||``に``||variables.変数 3でわったあまり を0にする||``をはめ込む
・``||math.計算||``から``||math.0 ÷ 1の余り||``を取り出して``||variables.変数 3でわったあまり を0にする||``にはめ込み、**右側の1**を**3**にする
・``||positions.ポジション||``から``||positions.positionのx(東西)座標||``を取り出して``||math.0 ÷ 1の余り||``の**左側の0**のところにはめ込む
・``||functions.みちをつくる||``の引数**開始位置**を取り出して``||positions.positionのx(東西)座標||``にはめ込む
・``||positions.開始位置のx(東西)座標||``の座標を、**Z(南北)**にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_make_variable1.gif">

```blocks

function みちをつくる (開始位置: Position) {
    _3でわったあまり = 開始位置.getValue(Axis.Z) % 3
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
}

```



## 条件分岐を追加する
条件分岐で**3でわったあまりが0のときにシーランタンを置く**プログラムを追加しよう！/p>
・``||logic.論理||``から``||logic.もし～なら||``を取り出して、``||functions.みちをつくる||``の**下**にはめ込む
・``||logic.論理||``から``||logic.0 = 0||``を取り出して、``||logic.もし～なら||``にはめ込む
・``||logic.もし 3でわったあまり = 0なら||``となるようにする
・引数**開始位置**の場所に、**シーランタン**をおくようにする

```blocks

function みちをつくる (開始位置: Position) {
    _3でわったあまり = 開始位置.getValue(Axis.Z) % 3
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
    if (_3でわったあまり == 0) {
        blocks.place(SEA_LANTERN, 開始位置)
    }
}

```



## くりかえす数を考える
ステージにつくまでくりかえし``||functions.みちをつくる||``を呼び出すにはどうすればいいのか考えよう！
・ステージにつくまでは、``||variables.開始位置||``の場所には**水がある**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_testfor1_1.png">
・ステージにみちがつながると、``||variables.開始位置||``の場所には**水がない**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_testfor1_2.png">
**もし水が**``||variables.開始位置||``**にあるならくりかえす**とすればうまくいきそうです！



## くりかえしを作る
チャットでsetと入力したときに、``||variables.開始位置||``にあるブロックが水ならばくりかえし``||functions.みちをつくる||``を呼び出そう
・``||player.チャットコマンドsetを入力した時||``に``||loops.もし～なら くりかえし||``をはめこむ
・``||player.チャットコマンドsetを入力した時||``に``||loops.もし～なら くりかえし||``をはめこむ
・``||blocks.ブロック||``から``||blocks.～が(~0, ~0, ~0)に存在する||``をとりだして、条件にはめこむ
・ブロックの種類を**水**にして、座標に``||variables.開始位置||``をはめこむ
・``||functions.関数||``から``||functions.呼び出し みちをつくる||``をとりだしてはめこみ、引数に``||variables.開始位置||``をはめこむ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_loop1.gif">


```blocks

player.onChat("set", function () {
    開始位置 = world(83, 62, 91)
    while (blocks.testForBlock(WATER, 開始位置)) {
        みちをつくる(開始位置)
    }
})
function みちをつくる (開始位置: Position) {
    _3でわったあまり = 開始位置.getValue(Axis.Z) % 3
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
    if (_3でわったあまり == 0) {
        blocks.place(SEA_LANTERN, 開始位置)
    }
}

```



## 変数に入った座標を動かす
``||variables.開始位置||``を、つぎにブロックをならべはじめる場所に動くよう、**自分で考えてプログラミングしよう**！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_move_variable1.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_positions_add1.png">


```blocks

player.onChat("set", function () {
    開始位置 = world(83, 62, 91)
    while (blocks.testForBlock(WATER, 開始位置)) {
        みちをつくる(開始位置)
        開始位置 = positions.add(
        開始位置,
        pos(0, -1, 1)
        )
    }
})
function みちをつくる (開始位置: Position) {
    _3でわったあまり = 開始位置.getValue(Axis.Z) % 3
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(-2, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(2, 4, 0)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(-1, 1, 0)
    ),
    positions.add(
    開始位置,
    pos(1, 3, 0)
    ),
    FillOperation.Replace
    )
    if (_3でわったあまり == 0) {
        blocks.place(SEA_LANTERN, 開始位置)
    }
}

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「set」と入力してガラスのカベを並べよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson8/L8_complete1.gif">
<br></br>
できあがったのを確認したら、**村人に話しかけよう**
