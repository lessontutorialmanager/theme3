# 向こう側まで橋をのばそう！

```blocks
    let スタート座標: Position = null
    function 橋をつくる (座標: Position) {
        blocks.fill(
        PLANKS_OAK,
        座標,
        positions.add(
        座標,
        pos(0, 0, 2)
        ),
        FillOperation.Replace
        )
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 0)
        ))
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 2)
        ))
    }
    player.onChat("run", function () {
        スタート座標 = world(-72, 59, 79)
        while (blocks.testForBlock(AIR, スタート座標)) {
            橋をつくる(スタート座標)
            スタート座標 = positions.add(
            スタート座標,
            pos(-1, 0, 0)
            )
        }
    })

```

```template
player.onChat("run", function () {
        スタート座標 = world(-72, 59, 79)
    })
```

## 向こう側まで橋をのばそう！ @unplugged
関数を使って便利に橋を作ろう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_complete.gif">



## 目標
関数を使って、進みたい先が空気ブロックなら橋をのばしていくようにしよう！<br>
・チャットコマンドで「run」と入力すると、進みたい方向が空気ブロックの間、くり返し橋をのばす<br>
・橋はオークの板材、オークのフェンスを使う<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_complete.gif">



## 手順を考える
まず、``||variables.スタート座標||``に入った場所が空気ブロックかどうか調べます<br>
もし空気ブロックなら、その位置に関数``||functions.橋をつくる||``を使ってブロックを1列ならべます<br>
これを``||variables.スタート座標||``が空気ブロックでなくなるまでくり返せば、向こう側まで橋をのばせそうです！<br>
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
下の画像をヒントに、**オークの板材**が**南に3ブロック**ならび、その1ブロック上の両はしに**オークのフェンス**を置くように、座標を自分で考えよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_set_coordinates.gif">

```blocks
function 橋をつくる (座標: Position) {
        blocks.fill(
        PLANKS_OAK,
        座標,
        positions.add(
        座標,
        pos(0, 0, 2)
        ),
        FillOperation.Replace
        )
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 0)
        ))
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 2)
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
➁「スタート座標」の位置を1ブロック**西**に変える<br>

```blocks
    let スタート座標: Position = null
    function 橋をつくる (座標: Position) {
        blocks.fill(
        PLANKS_OAK,
        座標,
        positions.add(
        座標,
        pos(0, 0, 2)
        ),
        FillOperation.Replace
        )
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 0)
        ))
        blocks.place(OAK_FENCE, positions.add(
        座標,
        pos(0, 1, 2)
        ))
    }
    player.onChat("run", function () {
        スタート座標 = world(-72, 59, 79)
        while (blocks.testForBlock(AIR, スタート座標)) {
            橋をつくる(スタート座標)
            スタート座標 = positions.add(
            スタート座標,
            pos(-1, 0, 0)
            )
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
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson5/L5_m1_complete.gif">
<br></br>
できあがったのを確認したら、橋がつながった先に移動しよう<br>

