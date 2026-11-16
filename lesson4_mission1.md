# お手本のとおりに家を建てよう！

```blocks
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

```template
let 作り始める位置: Position = null
player.onChat("set", function () {
    作り始める位置 = player.position()
})
player.onChat("run", function () {})
```

## お手本のとおりに家を建てよう！ @unplugged
村人のために、お手本のとおりに家を建てよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete1.png">



## 目標
お手本をよく見て、同じ形に家を建てよう！<br>
・チャットコマンドで「set」と入力して変数に作り始める位置の座標を入れる<br>
・チャットコマンドで「run」と入力すると家が作られる<br>
・ブロックは、丸石、オークの原木、オークの板材、オークのドアを使う<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete1.png">



## 手順を考える
まず、テラコッタブロックの上に立ってチャットで「set」と入力すると、変数``||variables.作り始める位置||``に座標が入ります<br>
その後チャットで「run」と入力すると、``||variables.作り始める位置||``に入った座標を基準にして、建物が作られます<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_run.gif">
<br></br>
まずは、壁の座標から考えていきましょう！<br>



## Step1 壁を作る
``||positions.(~0, ~0, ~0) + (~0, ~0, ~0)||``と``||variables.作り始める位置||``を組み合わせて、家の壁を作るプログラムを自分で考えてみよう！<br>
下の画像をヒントにしてみよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_wall.gif">

```blocks
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
})
```


## Step2 ドアを設置する
自分で位置を考えてオークのドアを設置しよう！<br>

```blocks
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
})
```


## Step3 屋根を作る
次に、屋根の並べ方を考えよう！<br>
下の画像をヒントにしよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_roof1.gif">

```blocks
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



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら家を建ててみよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson4/L4_complete1.gif">
<br></br>
できあがったのを確認したら、村人代表に話しかけよう<br>

