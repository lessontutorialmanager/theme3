# スティーブの顔を作ろう！

```blocks
let スタート座標: Position = null
function 顔 (開始位置: Position) {
    blocks.fill(
    LIGHT_GRAY_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 頭 (開始位置: Position) {
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 1)
    ))
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 8)
    ))
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 7, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 目 (開始位置: Position) {
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 2)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 3)
    ))
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 7)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 6)
    ))
}
function はなと口 (開始位置: Position) {
    blocks.fill(
    BROWN_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 3, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 3)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    WHITE_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 2, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 5)
    ),
    FillOperation.Replace
    )
}
player.onChat("run", function () {
    スタート座標 = world(57, 71, 132)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標)
        頭(スタート座標)
        目(スタート座標)
        はなと口(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})

```

```template

let スタート座標: Position = null
player.onChat("run", function () {
    スタート座標 = world(60, 71, 132)
})

```

## スティーブの顔をつくろう！ @unplugged
スティーブの形にブロックを並べよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete1.gif">



## 目標
**スティーブの顔**の形にブロックを並べよう！<br>
・チャットコマンドで「run」と入力すると、スティーブの顔の形にブロックを並べる<br>
・たて、横、高さが**8ブロック**の大きさにする<br>
・用意してある変数``||variables.スタート座標||``を基準にブロックを並べる<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face1.png">



## 手順を考える
顔の形にブロックを並べるとプログラムが長くなってしまうので、``||functions.関数||``を作って、顔のパーツごとにプログラムをわけよう！<br>
・4つの関数``||functions.顔||``、``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``を作成する<br>
・それぞれの関数の中で、顔のパーツを並べるプログラムを用意する<br>
・使うブロックは、下の画像を確認しよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face1_with_color.png">



## Step1 関数を作る
4つの関数を作ろう！<br>
・4つの関数``||functions.顔||``、``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``を作成する<br>
・関数には、**座標**の引数**開始位置**を作成する<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_make_functions.gif">

```blocks

function 顔 (開始位置: Position) {
}
function 頭 (開始位置: Position) {
}
function 目 (開始位置: Position) {
}
function はなと口 (開始位置: Position) {
}


```



## Step2 顔を作る①
**開始位置**を基準にしてブロックを並べられるように準備しよう！<br>
・``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を取り出して、関数``||functions.顔||``にはめ込む<br>
・ブロックの種類を**薄灰色(うすはいいろ)のテラコッタ**にする<br>
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して、**範囲の始まり**と**範囲の終わり**にはめ込む<br>
・``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``の**左**に、関数``||functions.顔||``の**開始位置**をはめ込む<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_fill_blocks.gif">

```blocks

function 顔 (開始位置: Position) {
    blocks.fill(
    LIGHT_GRAY_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(0, 0, 0)
    ),
    FillOperation.Replace
    )
}

```


## Step2 顔を作る➁
ブロックを顔の形に並べるために、座標の考え方をおさらいしよう！<br>
``||positions.開始位置 + (~0, ~0, ~0)||``の``||positions.(~0, ~0, ~0)||``の数字をどのようにすれば良いでしょう？<br>
たとえば、下の画像の**黄色**の部分は、基準から**上に8ブロック**、**南に8ブロック**の位置なので、``||positions.開始位置 + (~0, ~8, ~8)||``となります！<br>
このように、**スティーブの顔のまわりに書かれている数字を参考にして、範囲の始まりと範囲の終わりを考えてみよう！**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_coordinates.png">



## Step2 顔を作る③
先ほどの考えをもとにして、**範囲の始まり**と**範囲の終わり**の座標を、**自分で考えてプログラミングしよう！**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face1.png">

```blocks

function 顔 (開始位置: Position) {
    blocks.fill(
    LIGHT_GRAY_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}

```


## Step3 ほかのパーツを並べる
同じように、``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``のプログラミングを**自分で考えてやってみよう！**<br>
使うブロックは以下を確認しよう<br>
・``||functions.頭||``：黒色のテラコッタ<br>
・``||functions.目||``：白色のコンクリート、青色のコンクリート<br>
・``||functions.はなと口||``：茶色のテラコッタ、白色のテラコッタ、黒色のテラコッタ<br>
※ブロックを**1つ**だけおきたいときは、``||blocks.ブロック||``の``||blocks.ブロックを(~0, ~0, ~0)に置く||``を使おう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face1.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face1_with_color.png">

```blocks

function 頭 (開始位置: Position) {
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 1)
    ))
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 8)
    ))
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 7, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 目 (開始位置: Position) {
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 2)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 3)
    ))
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 7)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 6)
    ))
}
function はなと口 (開始位置: Position) {
    blocks.fill(
    BROWN_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 3, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 3)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    WHITE_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 2, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 5)
    ),
    FillOperation.Replace
    )
}

```


## Step4 関数を実行する①
``||player.チャットコマンドrunを入力した時||``を入力した時に関数を呼び出して実行できるようにしよう<br>
・``||functions.関数||``から``||functions.呼び出し 顔||``、``||functions.呼び出し 頭||``、``||functions.呼び出し 目||``、``||functions.呼び出し はなと口||``を取り出して、``||player.チャットコマンドrunを入力した時||``にはめ込む<br>
・引数をすべて``||variables.スタート座標||``に変更する<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_execute.png">



## Step4 関数を実行する➁
今のままでは平たい顔になってしまうので、**作った顔をくりかえし並べて厚くしよう！**<br>
①関数を呼び出して顔を作る→➁``||variables.スタート座標||``の位置を**東に1ブロック**動かすを**8回**くり返そう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_repeating.gif">



## Step4 関数を実行する③
``||variables.スタート座標||``の位置を**東に1ブロック**動かそう！<br>
・``||variables.変数||``から``||variables.変数 スタート座標を0にする||``を取り出して、``||player.チャットコマンドrunを入力した時||``の**一番下**にはめ込む<br>
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``を取り出して、``||variables.変数 スタート座標を0にする||``にはめ込む<br>
・``||variables.変数||``から``||variables.スタート座標||``を取り出して、``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``の**左側**にはめ込む<br>
・``||variables.スタート座標||``に入った座標が**東に1ブロック**移動するように、**自分で考えてプログラミングしよう！**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_shift_coordinates.png">

```blocks

let スタート座標: Position = null
player.onChat("run", function () {
    スタート座標 = world(57, 71, 132)
        顔(スタート座標)
        頭(スタート座標)
        目(スタート座標)
        はなと口(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
})
function 顔 (開始位置: Position) {
    blocks.fill(
    LIGHT_GRAY_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 頭 (開始位置: Position) {
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 1)
    ))
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 8)
    ))
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 7, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 目 (開始位置: Position) {
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 2)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 3)
    ))
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 7)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 6)
    ))
}
function はなと口 (開始位置: Position) {
    blocks.fill(
    BROWN_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 3, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 3)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    WHITE_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 2, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 5)
    ),
    FillOperation.Replace
    )
}


```




## Step4 関数を実行する④
①関数を呼び出して顔を作る→➁``||variables.スタート座標||``の位置を**東に1ブロック**動かすを**8回**くり返すように**自分で考えてプログラミングしよう！**<br>

```blocks

let スタート座標: Position = null
player.onChat("run", function () {
    スタート座標 = world(57, 71, 132)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標)
        頭(スタート座標)
        目(スタート座標)
        はなと口(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})
function 顔 (開始位置: Position) {
    blocks.fill(
    LIGHT_GRAY_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 頭 (開始位置: Position) {
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 1)
    ))
    blocks.place(BLACK_TERRACOTTA, positions.add(
    開始位置,
    pos(0, 6, 8)
    ))
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 7, 1)
    ),
    positions.add(
    開始位置,
    pos(0, 8, 8)
    ),
    FillOperation.Replace
    )
}
function 目 (開始位置: Position) {
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 2)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 3)
    ))
    blocks.place(WHITE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 7)
    ))
    blocks.place(BLUE_CONCRETE, positions.add(
    開始位置,
    pos(0, 4, 6)
    ))
}
function はなと口 (開始位置: Position) {
    blocks.fill(
    BROWN_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 3, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    BLACK_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 1, 3)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    WHITE_TERRACOTTA,
    positions.add(
    開始位置,
    pos(0, 2, 4)
    ),
    positions.add(
    開始位置,
    pos(0, 2, 5)
    ),
    FillOperation.Replace
    )
}


```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったらチャットで「run」と入力してスティーブの顔の形にブロックを並べよう！<br>
うまくいかなかったときは、**座標を自分で修正してみよう**<br>
できあがったら、**村人に話しかけよう**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete1.gif">


