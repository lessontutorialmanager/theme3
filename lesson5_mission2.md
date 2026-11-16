# 向こう側まで橋をのばそう

```blocks
let Z座標 = 0
let スタート座標: Position = null
function 橋をつくる (座標: Position) {
    blocks.fill(
    PLANKS_OAK,
    座標,
    positions.add(
    座標,
    pos(2, 0, 0)
    ),
    FillOperation.Replace
    )
    if (Z座標 % 3 == 0) {
        blocks.place(GLOWSTONE, positions.add(
        座標,
        pos(1, 0, 0)
        ))
    }
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(0, 1, 0)
    ))
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(2, 1, 0)
    ))
}
player.onChat("run", function () {
    スタート座標 = world(-96, 59, 78)
    Z座標 = スタート座標.getValue(Axis.Z)
    while (blocks.testForBlock(AIR, スタート座標)) {
        橋をつくる(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(0, 0, -1)
        )
        Z座標 = スタート座標.getValue(Axis.Z)
    }
})


```

```template
let スタート座標: Position = null
let Z座標 = 0
player.onChat("run", function () {
    スタート座標 = world(-96, 59, 78)
    Z座標 = スタート座標.getValue(Axis.Z)
})

```

## 向こう側まで橋をのばそう！ @unplugged
足もとに3ブロックに1回明かりを置くようにしよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_complete.gif">



## 目標
関数を使って、進みたい先が空気ブロックなら橋をのばしていくようにしよう！<br>
・チャットコマンドで「run」と入力すると、進みたい方向が空気ブロックの間、くり返し橋をのばす<br>
・橋はオークの板材、オークのフェンスを使う<br>
・3ブロックに1回足元の床をグロウストーンにする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_complete.gif">



## 手順を考える
まずはさっきと同じように、``||variables.スタート座標||``に入った場所が空気ブロックなら、橋をのばすプログラムを作っていこう！<br>
その後、3ブロックに1回足もとにグロウストーンを置く方法を足そう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_1.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_2.png">
<br></br>
まずは、指定した座標に橋を1ブロック分作る関数を用意しよう！<br>



## Step1 関数を用意する
引数**座標**を持った関数``||functions.橋をつくる||``を用意しよう！<br>
・``||functions.関数||``を開いて、**関数を作成する**を押す<br>
・関数の名前を**橋をつくる**にする<br>
・上に並んでいるボタンのうち**ポジション**(一番右)を押して、座標を引数にする<br>
・引数の名前を**座標**にする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_make_function.gif">



## Step2 ブロックを並べる①
オークの板材が並ぶように準備しよう！<br>
・``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を取り出して``||functions.橋をつくる||``にはめ込み、ブロックの種類を**オークの板材**にする<br>
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して``||blocks.ブロックを並べる||``の**範囲の終わり**にはめ込む<br>
・**座標**を下のようにはめ込む<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_set_parameter.gif">



## Step3 ブロックを並べる➁
オークのフェンスが並ぶように準備しよう！<br>
・``||blocks.ブロック||``から``||blocks.ブロックを(~0, ~0, ~0)に置く||``を**2つ**取り出して``||functions.橋をつくる||``にはめ込み、ブロックの種類を**オークのフェンス**にする<br>
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を**2つ**取り出して``||blocks.ブロックを(~0, ~0, ~0)に置く||``にはめ込む<br>
・**座標**を下のようにはめ込む<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_set_parameter2.gif">




## Step4 ブロックを並べる③
座標を考えよう！<br>
下の画像をヒントに、**オークの板材**が**東に3ブロック**ならび、その1ブロック上の両はしに**オークのフェンス**を置くように、座標を自分で考えよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_set_coordinates.gif">

```blocks
function 橋をつくる (座標: Position) {
    blocks.fill(
    PLANKS_OAK,
    座標,
    positions.add(
    座標,
    pos(2, 0, 0)
    ),
    FillOperation.Replace
    )
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(0, 1, 0)
    ))
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(2, 1, 0)
    ))
}
```



## Step5 条件分岐を考える①
下の図のように、**スタート座標の場所が空気ブロック**なら、その座標で``||functions.橋をつくる||`` を実行するようにしよう！<br>
今回は、スタート座標の場所が空気ブロックの間くりかえすので、``||loops.もし～ならくりかえし||``を使うとよさそうです！！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_3.png">



## Step6 条件分岐を考える➁
``||loops.もし～ならくりかえし||``と``||blocks.～が(~0, ~0, ~0)に存在する||``を使って、``||player.チャットコマンドrunを入力した時||``に条件分岐を自分で考えてプログラミングしよう！<br>
①「スタート座標」の位置で``||functions.橋をつくる||``を実行する<br>
➁「スタート座標」の位置を1ブロック**北**に変える<br>

```blocks
let Z座標 = 0
let スタート座標: Position = null
function 橋をつくる (座標: Position) {
    blocks.fill(
    PLANKS_OAK,
    座標,
    positions.add(
    座標,
    pos(2, 0, 0)
    ),
    FillOperation.Replace
    )
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(0, 1, 0)
    ))
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(2, 1, 0)
    ))
}
player.onChat("run", function () {
    スタート座標 = world(-96, 59, 78)
    Z座標 = スタート座標.getValue(Axis.Z)
    while (blocks.testForBlock(AIR, スタート座標)) {
        橋をつくる(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(0, 0, -1)
        )
    }
})
```


## Step7 3ブロックに1回グロウストーンを置く考え方①
このプログラムをさらに改造して、**3ブロックに1回足もとにグロウストーンを置く**ようにしましょう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_1.png">



## Step7 3ブロックに1回グロウストーンを置く考え方➁
○回に1回何かを実行したいとき、プログラミングではよく**わり算のあまりを使った条件分岐**を使います！<br>
たとえば、下の図を見ると、**Z座標を3でわったあまり**が**0、1、2、0、1、2、…とくりかえしている**ことがわかります<br>
この性質を使って、**Z座標を3でわったあまりが0のときにグロウストーンを置く**ようにすれば3回に1回置くことができそうです！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_2.png">



## Step8 3ブロックに1回グロウストーンを置く考え方③
フローチャートでやることを確認しましょう！<br>
・``||functions.橋をつくる||``に条件分岐で**Z座標を3でわったあまりが0のときにグロウストーンを置く**プログラムを追加<br>
・``||variables.スタート座標||``の数字が変わったときに``||variables.Z座標||``の数字も新しくする<br>
の2つをすれば良さそうです！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_3.png">



## Step9 条件分岐を追加する①
``||functions.橋をつくる||``に条件分岐で**Z座標を3でわったあまりが0のときにグロウストーンを置く**プログラムを追加しよう！/p>
・``||logic.論理||``から``||logic.もし～なら||``と``||logic.0 = 0||``を取り出して、``||blocks.ブロックを並べる||``の**下**にはめ込む<br>
・``||math.計算||``から``||math.0 / 0の余り||``を取り出して``||logic.0 = 0||``の**左**にはめ込む<br>
・``||math.Z座標 / 3の余り||``となるようにする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_conditional.gif">



## Step10 条件分岐を追加する➁
条件分岐の中にプログラムを追加しよう！/p>
・``||blocks.ブロックを(~0, ~0, ~0)に置く||``、``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``、**座標**を使って、足もとにグロウストーンを置くようにしよう！<br>
どのようにすれば良さそうか自分で考えてプログラミングしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_1.png">

```blocks
let Z座標 = 0
function 橋をつくる (座標: Position) {
    blocks.fill(
    PLANKS_OAK,
    座標,
    positions.add(
    座標,
    pos(2, 0, 0)
    ),
    FillOperation.Replace
    )
    if (Z座標 % 3 == 0) {
        blocks.place(GLOWSTONE, positions.add(
        座標,
        pos(1, 0, 0)
        ))
    }
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(0, 1, 0)
    ))
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(2, 1, 0)
    ))
}

```


## Step11 変数の更新
変数``||variables.スタート座標||``を動かした時に、``||variables.Z座標||``の数字も新しくなるようにしよう！<br>
・``||variables.変数 Z座標を0にする||``を取り出して、``||変数 スタート座標をスタート座標 + (~0, ~0, ~-1)にする||``の**下**にはめ込む<br>
・``||positions.ポジション||``から``||positions.positionのx(東西)方向||``を取り出して、``||variables.変数 Z座標を0にする||``にはめ込む<br>
・設定を**スタート座標のz(南北)方向**にする<br>

```blocks
let Z座標 = 0
let スタート座標: Position = null
function 橋をつくる (座標: Position) {
    blocks.fill(
    PLANKS_OAK,
    座標,
    positions.add(
    座標,
    pos(2, 0, 0)
    ),
    FillOperation.Replace
    )
    if (Z座標 % 3 == 0) {
        blocks.place(GLOWSTONE, positions.add(
        座標,
        pos(1, 0, 0)
        ))
    }
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(0, 1, 0)
    ))
    blocks.place(OAK_FENCE, positions.add(
    座標,
    pos(2, 1, 0)
    ))
}
player.onChat("run", function () {
    スタート座標 = world(-96, 59, 78)
    Z座標 = スタート座標.getValue(Axis.Z)
    while (blocks.testForBlock(AIR, スタート座標)) {
        橋をつくる(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(0, 0, -1)
        )
        Z座標 = スタート座標.getValue(Axis.Z)
    }
})


```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったらチャットで「run」と入力しよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m2_complete.gif">
<br></br>
できあがったのを確認したら、橋がつながった先に移動しよう<br>

