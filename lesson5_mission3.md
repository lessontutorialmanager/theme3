# 地面まで階段をのばそう

```blocks
let Z座標 = 0
let スタート座標: Position = null
function 階段をつくる (座標: Position) {
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
    スタート座標 = world(-96, 59, 29)
    Z座標 = スタート座標.getValue(Axis.Z)
    while (blocks.testForBlock(AIR, スタート座標)) {
        階段をつくる(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(0, -1, -1)
        )
        Z座標 = スタート座標.getValue(Axis.Z)
    }
})


```

```template
let スタート座標: Position = null
let Z座標 = 0
player.onChat("run", function () {
    スタート座標 = world(-96, 59, 29)
    Z座標 = スタート座標.getValue(Axis.Z)
})
```

## 地面まで階段をのばそう！ @unplugged
地面に着くまで階段をのばそう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_complete.gif">



## 目標
関数を使って、進みたい先が空気ブロックなら階段をのばしていくようにしよう！<br>
・チャットコマンドで「run」と入力すると、進みたい方向が空気ブロックの間、くり返し階段をのばす<br>
・階段はオークの板材、オークのフェンスを使う<br>
・3ブロックに1回足元の床をグロウストーンにする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_complete.gif">



## 手順を考える
考え方は先ほどの橋と同じです！<br>
``||variables.スタート座標||``の動かし方だけが変わるので、下の画像でどう変えれば良いか考えてみよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_1.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_2.png">



## Step1 関数を用意する
引数**座標**を持った関数``||functions.階段をつくる||``を用意しよう！<br>
・``||functions.関数||``を開いて、**関数を作成する**を押す<br>
・関数の名前を**階段をつくる**にする<br>
・上に並んでいるボタンのうち**ポジション**(一番右)を押して、座標を引数にする<br>
・引数の名前を**座標**にする<br>



## Step2 関数の中身を作る
関数``||functions.階段をつくる||``に、``||blocks.ブロックを並べる||``や``||blocks.ブロックを(~0, ~0, ~0)に置く||``を使って、1段分床とフェンスが並ぶようにしよう！<br>
下の画像をヒントに、**オークの板材**が**東に3ブロック**ならび、その1ブロック上の両はしに**オークのフェンス**を置くように、座標を自分で考えよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_set_coordinates.gif">




## Step3 3回に1回グロウストーンを置くように条件分岐を作る
**3ブロックに1回**グロウストーンを床に置くように条件分岐しよう！<br>
``||functions.階段をつくる||``に条件分岐で**Z座標を3でわったあまりが0のときにグロウストーンを置く**プログラムを追加しよう！/p>
・``||logic.論理||``から``||logic.もし～なら||``と``||logic.0 = 0||``を取り出して、``||blocks.ブロックを並べる||``の**下**にはめ込む<br>
・``||math.計算||``から``||math.0 / 0の余り||``を取り出して``||logic.0 = 0||``の**左**にはめ込む<br>
・``||math.Z座標 / 3の余り||``となるようにする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_2.png">



## Step4 プログラムを修正する
``||loops.もし～ならくりかえし||``と``||blocks.～が(~0, ~0, ~0)に存在する||``を使って、``||player.チャットコマンドrunを入力した時||``に条件分岐を自分で考えてプログラミングしよう！<br>
``||variables.スタート座標||``をどのように動かせばよいか、自分で考えてプログラミングしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_1.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_2.png">



## Step5 変数の更新
変数``||variables.スタート座標||``を動かした時に、``||variables.Z座標||``の数字も新しくなるようにしよう！<br>

```blocks
let Z座標 = 0
let スタート座標: Position = null
function 階段をつくる (座標: Position) {
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
    スタート座標 = world(-96, 59, 29)
    Z座標 = スタート座標.getValue(Axis.Z)
    while (blocks.testForBlock(AIR, スタート座標)) {
        階段をつくる(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(0, -1, -1)
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
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m3_complete.gif">
<br></br>
できあがったのを確認したら、階段がつながった先に移動しよう<br>

