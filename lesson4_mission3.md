# 引数でブロックを変えられるようにしよう！

```blocks
let 作り始める位置: Position = null
player.onChat("run", function (num1) {
    かべ()
    if (num1 == 1) {
        やね1(PLANKS_OAK)
    } else if (num1 == 2) {
        やね1(CHERRY_PLANKS)
    } else if (num1 == 3) {
        やね2(PLANKS_OAK)
    } else {
        やね2(CHERRY_PLANKS)
    }
})
player.onChat("set", function () {
    作り始める位置 = player.position()
})
function やね2 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 1)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 1)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(3, 7, 1)
    ),
    positions.add(
    作り始める位置,
    pos(3, 7, 5)
    ),
    FillOperation.Replace
    )
}
function かべ () {
    blocks.fill(
    COBBLESTONE,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 0, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 1, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 3, 4)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.place(OAK_DOOR, positions.add(
    作り始める位置,
    pos(3, 1, 1)
    ))
}
function やね1 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 0)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 4)
    ),
    FillOperation.Replace
    )
}

```

```template
let 作り始める位置: Position = null
player.onChat("run", function (num1) {
    かべ()
    if (num1 == 1) {
        やね1()
    } else {
        やね2()
    }
})
player.onChat("set", function () {
    作り始める位置 = player.position()
})
function やね2 () {
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(0, 4, 1)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(2, 6, 1)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(3, 7, 1)
    ),
    positions.add(
    作り始める位置,
    pos(3, 7, 5)
    ),
    FillOperation.Replace
    )
}
function かべ () {
    blocks.fill(
    COBBLESTONE,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 0, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 1, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 3, 4)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.place(OAK_DOOR, positions.add(
    作り始める位置,
    pos(3, 1, 1)
    ))
}
function やね1 () {
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(0, 4, 0)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(2, 6, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 4)
    ),
    FillOperation.Replace
    )
}
```

## 引数でブロックを変えられるようにしよう！ @unplugged
引数を使って、ブロックの種類を変えて家を建てられるようにしよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete3.png">



## 目標
今回つくる建物は、先ほど作ったプログラムの屋根の部分を「サクラの板材」に変えただけです<br>
``||function.やね1||``、``||function.やね2||``の2つの関数に引数を渡せるようにして、条件分岐で屋根に使うブロックを変えられるようにしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete3.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete1.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete2.png">



## Step1 引数を使えるようにする①
``||function.やね1||``、``||function.やね2||``に引数を渡せるように用意しよう！<br>
・``||function.やね1||``を右クリック(タブレットの場合は長押し)してメニューを開き、「関数の編集」を押す<br>
・左から3番目の「数値(電卓のマーク)」ボタンを押し、名前を「ブロック」にする<br>
※``||function.やね1||``、``||function.やね2||``の両方にしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_make_parameter.gif">



## Step2 引数を使えるようにする➁
関数に渡されたブロックの種類が、``||blocks.ブロックを並べる||``に設定されるようにしよう<br>
・関数の名前の横に追加された「ブロック」を取り出して、すべての``||blocks.ブロックを並べる||``のブロックの種類の部分にはめ込む<br>
※``||function.やね1||``、``||function.やね2||``の両方にしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_set_parameter.gif">

```blocks
function やね2 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 1)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 1)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(3, 7, 1)
    ),
    positions.add(
    作り始める位置,
    pos(3, 7, 5)
    ),
    FillOperation.Replace
    )
}
function やね1 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 0)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 4)
    ),
    FillOperation.Replace
    )
}
```



## 引数の役割
``||function.呼び出し やね1||``を見てみると、「1」という数字が表示されています<br>
<br></br>
<img width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_parameter2.png">
<br></br>
ここに好きなブロックの種類をはめ込むと、``||function.やね1||``の中の「ブロック」の部分に、呼び出しにはめ込んだブロックの種類が設定されます<br>
<br></br>
<img width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_parameter.png">
<br></br>
こうすることで、``||function.やね1||``と条件分岐を組み合わせれば、屋根に使うブロックの種類をひとつの関数で使い分けることができます！<br>



## Step3 条件分岐を設定する
``||player.チャットコマンドrunを入力した時||``の条件分岐を設定し直そう！<br>
・``||variables.num1||``が1のとき：``||function.やね1||``に引数「オークの板材」を渡す<br>
・``||variables.num1||``が2のとき：``||function.やね1||``に引数「サクラの板材」を渡す<br>
・``||variables.num1||``が3のとき：``||function.やね2||``に引数「オークの板材」を渡す<br>
・``||variables.num1||``がそれ以外のとき：``||function.やね2||``に引数「サクラの板材」を渡す<br>

```blocks
let 作り始める位置: Position = null
player.onChat("run", function (num1) {
    かべ()
    if (num1 == 1) {
        やね1(PLANKS_OAK)
    } else if (num1 == 2) {
        やね1(CHERRY_PLANKS)
    } else if (num1 == 3) {
        やね2(PLANKS_OAK)
    } else {
        やね2(CHERRY_PLANKS)
    }
})
player.onChat("set", function () {
    作り始める位置 = player.position()
})
function やね2 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 1)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 1)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(3, 7, 1)
    ),
    positions.add(
    作り始める位置,
    pos(3, 7, 5)
    ),
    FillOperation.Replace
    )
}
function かべ () {
    blocks.fill(
    COBBLESTONE,
    positions.add(
    作り始める位置,
    pos(1, 0, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 0, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    作り始める位置,
    pos(2, 1, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 3, 4)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 1)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(1, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(1, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    LOG_OAK,
    positions.add(
    作り始める位置,
    pos(5, 1, 5)
    ),
    positions.add(
    作り始める位置,
    pos(5, 3, 5)
    ),
    FillOperation.Replace
    )
    blocks.place(OAK_DOOR, positions.add(
    作り始める位置,
    pos(3, 1, 1)
    ))
}
function やね1 (ブロック: number) {
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(0, 4, 0)
    ),
    positions.add(
    作り始める位置,
    pos(6, 4, 6)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(1, 5, 1)
    ),
    positions.add(
    作り始める位置,
    pos(5, 5, 5)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    ブロック,
    positions.add(
    作り始める位置,
    pos(2, 6, 2)
    ),
    positions.add(
    作り始める位置,
    pos(4, 6, 4)
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
ゲーム画面にもどったら、1つ目のテラコッタブロックの上に立って「set」した後、チャットで「run 2」と入力しよう<br>
もうひとつのテラコッタブロックの上に立って「set」したら、今度はチャットで「run 4」と入力しよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete3.png">
<br></br>
できあがったのを確認したら、村人代表に話しかけよう<br>
