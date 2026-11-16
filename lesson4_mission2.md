# 関数で屋根の形を変えられるようにしよう！

```blocks
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

```template
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {
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
})
```

## 関数で屋根の形を変えられるようにしよう！ @unplugged
家の部分を関数に分けて、屋根の形を変えられるようにしよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete2.png">



## 目標
今回作る建物は、先ほどと壁の形は同じで、屋根の形が変わっただけです<br>
関数を使って、壁を作る関数と屋根を作る関数に分けて、条件分岐で屋根の種類をえらべるようにしよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete1.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete2.png">



## Step1 関数を作る
``||function.かべ||``、``||function.やね1||``、``||function.やね2||``の3つの関数を作ろう<br>
・``||function.関数||``を開いて「関数を作成する」を押し、上の3つの関数を作る<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_make_function.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_make_functions.png">

```blocks
function かべ () {
	
}
function やね1 () {
	
}
function やね2 () {
	
}
```



## Step2 関数に分ける
先ほどのミッションで作ったプログラムのうち、屋根を作るプログラムを``||function.やね1||``に、壁とドアを作るプログラムを``||function.かべ||``に移動させよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_set_function.gif">

```blocks
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



## Step3 新しい形の屋根をつくる
``||function.やね2||``に、新しい形の屋根を作るプログラムを作ろう！<br>
画像をみて、どんな順番で作ればよいか考えよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_roof1.gif">

```blocks
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
```



## 条件分岐を考える
チャットで「run 1」と入力したらこれまでの屋根の形で、「run 2」と入力したら新しい形で家が作られるように条件分岐しよう<br>
・``||variables.num1||``を作る<br>
・``||variables.num1||``が1なら``||function.やね1||``を、2なら``||function.やね2||``を呼び出す<br>



## Step4 条件分岐する
考えたことを元に、``||variables.num1||``に入った数で条件分岐しよう！<br>
・``||player.チャットコマンドrunを入力した時||``の⊕を押して``||variables.num1||``を作る<br>
・``||variables.num1||``が1なら``||function.やね1||``を、2なら``||function.やね2||``となるように条件分岐する<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_conditional.gif">


```blocks
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




## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、テラコッタブロックの上に立って「set」したあと、チャットで「run 2」と入力しよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete2.png">
<br></br>
できあがったのを確認したら、村人代表に話しかけよう<br>

