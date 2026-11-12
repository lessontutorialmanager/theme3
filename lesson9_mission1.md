# アイテムやかべをランダムにしよう！

```blocks

function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function かべをつくる () {
    blocks.fill(
    AIR,
    world(79, 49, 109),
    world(87, 50, 116),
    FillOperation.Replace
    )
    for (let index = 0; index < 3; index++) {
        開始位置 = randpos(
        world(79, 49, 109),
        world(86, 49, 116)
        )
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS_PANE,
        開始位置,
        positions.add(
        開始位置,
        pos(1, 1, 0)
        ),
        FillOperation.Replace
        )
    }
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            とびらをあける()
            ランダムなアイテムをわたす()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            かべをつくる()
            とびら = false
        }
    }
})
function ランダムなアイテムをわたす () {
    for (let index = 0; index < 2; index++) {
        ランダムな数 = randint(1, 8)
        if (ランダムな数 == 1) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            NETHERITE_SWORD,
            1
            )
            player.say("ネザライトの剣をてにいれた！")
        } else if (ランダムな数 == 2 || ランダムな数 == 3) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            SHIELD,
            1
            )
            player.say("盾をてにいれた！")
        } else if (ランダムな数 == 4 || ランダムな数 == 5) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            IRON_SWORD,
            1
            )
            player.say("鉄の剣をてにいれた！")
        } else if (ランダムな数 == 6 || ランダムな数 == 7) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            BREAD,
            3
            )
            player.say("パンをてにいれた！")
        } else if (ランダムな数 == 8) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            GOLDEN_APPLE,
            1
            )
            player.say("金のリンゴをてにいれた！")
        }
    }
}
let ランダムな数 = 0
let 開始位置: Position = null
let とびら = false
とびら = false




```

```template

function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    NETHERITE_SWORD,
    1
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
    player.say("けんとたてをてにいれた！")
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            とびらをあける()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            とびら = false
        }
    }
})
let とびら = false
とびら = false

```

## アイテムやかべをランダムにしよう！ @unplugged
プレイヤーにランダムなアイテムをわたしたり、かべをランダムな位置に作ったりしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete1.gif">



## 目標(もくひょう)
プレイヤーにランダムなアイテムがわたされたり、モンスターとのあいだのランダムな場所にかべをつくったりできるようにしよう！
・新しく``||functions.ランダムなアイテムをわたす||``をつくり、ランダムなアイテムを2つプレイヤーにわたすようにする
・新しく``||functions.かべをつくる||``をつくり、ランダムな場所にかべをつくるようにする
・**白色の彩釉テラコッタ**の上に立ったときに``||functions.ランダムなアイテムをわたす||``を、**橙色の彩釉テラコッタ**の上に立ったときに``||functions.かべをつくる||``を呼び出すようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete1.gif">



## ランダムなアイテムをわたす方法を考える
ランダムなアイテムをわたす方法をかんがえよう！
①``||variables.ランダムな数||``という変数を作って、その中に**1～8のランダムな数**を入れる
②``||variables.ランダムな数||``に入った数によって条件分岐する
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_flow1.png">
これを、``||functions.ランダムなアイテムをわたす||``という関数の中に作りましょう！



## 関数と変数を作る
関数``||funcitons.ランダムなアイテムをわたす||``と、変数``||variables.ランダムな数||``を作って、変数の中に**乱数**を入れよう！
※復習　乱数：コンピューターがくじを引くようにランダムに選んだ数のこと
・``||functions.ランダムなアイテムをわたす||``を作る
・``||variables.ランダムな数||``を作り、``||variables.変数 ランダムな数 を0にする||``を``||functions.ランダムなアイテムをわたす||``にはめこむ
・``||math.計算||``から``||math.ランダムな数を選択||``を取り出して``||variables.変数 ランダムな数 を0にする||``にはめこむ
・ランダムな数を**1から8まで**にする
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_make_function_and_variable.gif">

```blocks

function ランダムなアイテムをわたす () {
    ランダムな数 = randint(1, 8)
}

```



## 条件分岐を作る
条件分岐を、下のヒントをもとに**自分で考えてプログラミング**しよう！
・``||variables.ランダムな数||``が**1**: ネザライトの剣をわたす
・``||variables.ランダムな数||``が**2または3**: 盾をわたす
・``||variables.ランダムな数||``が**4または5**: 鉄の剣をわたす
・``||variables.ランダムな数||``が**6または7**: パンを3つわたす
・``||variables.ランダムな数||``が**8**: 金のリンゴをわたす
「または」は、``||logics.論理||``のなかにあります！下の図を参考にしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_or.png">
・条件分岐の最後が「でなければ」になっているときは、⊕をおしたあとに⊖をおすと、「でなければもし」に変わります！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_elseif.gif">



## メッセージ送信する
「ネザライトの剣をてにいれた！」のように、手に入れたものをメッセージ送信するよう、**自分で考えてプログラミング**しよう！



## 2回くりかえす
プレイヤーにアイテムを**2つ**わたしたいので、ランダムな数を選んでプレイヤーに条件分岐するプログラムを**2回くりかえす**するように、**自分で考えてプログラミング**しよう！

```blocks

function ランダムなアイテムをわたす () {
    for (let index = 0; index < 2; index++) {
        ランダムな数 = randint(1, 8)
        if (ランダムな数 == 1) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            NETHERITE_SWORD,
            1
            )
            player.say("ネザライトの剣をてにいれた！")
        } else if (ランダムな数 == 2 || ランダムな数 == 3) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            SHIELD,
            1
            )
            player.say("盾をてにいれた！")
        } else if (ランダムな数 == 4 || ランダムな数 == 5) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            IRON_SWORD,
            1
            )
            player.say("鉄の剣をてにいれた！")
        } else if (ランダムな数 == 6 || ランダムな数 == 7) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            BREAD,
            3
            )
            player.say("パンをてにいれた！")
        } else if (ランダムな数 == 8) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            GOLDEN_APPLE,
            1
            )
            player.say("金のリンゴをてにいれた！")
        }
    }
}

```



## プログラムを修正する
前回のミッションで、``||functions.とびらをあける||``の中でアイテムをわたすようにプログラムしていました
修正して、**白色の彩釉テラコッタ**の上に立ったときに``||functions.ランダムなアイテムをわたす||``を呼び出すようにしよう！
・``||functions.とびらをあける||``の中の、アイテムをわたすプログラムとメッセージ送信のプログラムを消す
・``||logics.もし 白色の彩釉テラコッタが(~0, ~-1, ~0)に存在する なら||``の中に、``||functions.呼び出し ランダムなアイテムをわたす||``をはめこむ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_call_function1.gif">
これで、ランダムなアイテムをわたすプログラムが完成しました！



## ランダムな場所にかべを作る方法
つぎに、ランダムな場所にかべを作る方法を考えよう！
①**ワールド(79, 49, 109)からワールド(86, 49, 116)の中のランダムな座標**を変数``||variables.開始位置||``に入れる
②``||variables.開始位置||``を基準にして、**東に2ブロック**、**上に2ブロック**分の大きさで、**空色の色付きガラス板**を並べる
の2つをすれば良さそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_random_wall.gif">



## 関数と変数を作る
``||functions.かべをつくる||``と``||variables.開始位置||``を作って、変数の中にランダムな座標を入れよう！
・``||functions.かべをつくる||``という関数を作る
・``||variables.開始位置||``という変数を作り、``||variables.変数 開始位置 を0にする||``をはめ込む
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0)から(~0, ~0, ~0)の間のランダムな座標||``を取り出して``||variables.変数 開始位置 を0にする||``にはめ込む
・``||positions.ポジション||``から``||positions.ワールド(0, 0, 0)||``を**2つ**取り出して``||positions.(~0, ~0, ~0)から(~0, ~0, ~0)の間のランダムな座標||``にはめ込む
・座標を**ワールド(79, 49, 109)からワールド(86, 49, 116)**にする
これで、``||variables.開始位置||``の中に、ワールド(79, 49, 109)からワールド(86, 49, 116)の中のランダムな座標を入れるプログラムができました！

```blocks

function かべをつくる () {
    開始位置 = randpos(
    world(79, 49, 109),
    world(86, 49, 116)
    )
}

```



## ブロックを並べる
``||variables.開始位置||``を基準に、ブロックを並べるプログラムを**自分で考えてプログラミング**しよう！
・ブロックの種類: **空色の色付きガラス板**
・大きさ: ``||variables.開始位置||``を基準にして、**東に2ブロック**、**上に2ブロック**分
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_fill_glass.png">



## 3回くりかえす
ランダムな場所にかべを**3つ**作りたいので、ランダムな座標をえらんでかべを並べるプログラムを**3回くりかえす**ように、**自分で考えてプログラミング**しよう！

```blocks

function かべをつくる () {
    for (let index = 0; index < 3; index++) {
        開始位置 = randpos(
        world(79, 49, 109),
        world(86, 49, 116)
        )
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS_PANE,
        開始位置,
        positions.add(
        開始位置,
        pos(1, 1, 0)
        ),
        FillOperation.Replace
        )
    }
}

```



## かべを消す
今のままだと、ゲームをするたびにかべが3つ作られて、どんどんせまくなってしまいます…
かべを作る前に、のこっているかべを消すようにしよう！
・かべを並べるプログラムの**前**に、空気ブロックを``||positions.ワールド(79, 49, 109)||``から``||positions.ワールド(87, 49, 116)||``に並べる

```blocks

function かべをつくる () {
    blocks.fill(
    AIR,
    world(79, 49, 109),
    world(87, 50, 116),
    FillOperation.Replace
    )
    for (let index = 0; index < 3; index++) {
        開始位置 = randpos(
        world(79, 49, 109),
        world(86, 49, 116)
        )
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS_PANE,
        開始位置,
        positions.add(
        開始位置,
        pos(1, 1, 0)
        ),
        FillOperation.Replace
        )
    }
}

```



## プログラムを修正する
橙色の彩釉テラコッタの上に立ったときに、``||functions.かべをつくる||``を呼び出すように、**自分で考えてプログラミングしよう**！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            とびらをあける()
            ランダムなアイテムをわたす()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            かべをつくる()
            とびら = false
        }
    }
})
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function かべをつくる () {
    blocks.fill(
    AIR,
    world(79, 49, 109),
    world(87, 50, 116),
    FillOperation.Replace
    )
    for (let index = 0; index < 3; index++) {
        開始位置 = randpos(
        world(79, 49, 109),
        world(86, 49, 116)
        )
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS_PANE,
        開始位置,
        positions.add(
        開始位置,
        pos(1, 1, 0)
        ),
        FillOperation.Replace
        )
    }
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function ランダムなアイテムをわたす () {
    for (let index = 0; index < 2; index++) {
        ランダムな数 = randint(1, 8)
        if (ランダムな数 == 1) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            NETHERITE_SWORD,
            1
            )
            player.say("ネザライトの剣をてにいれた！")
        } else if (ランダムな数 == 2 || ランダムな数 == 3) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            SHIELD,
            1
            )
            player.say("盾をてにいれた！")
        } else if (ランダムな数 == 4 || ランダムな数 == 5) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            IRON_SWORD,
            1
            )
            player.say("鉄の剣をてにいれた！")
        } else if (ランダムな数 == 6 || ランダムな数 == 7) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            BREAD,
            3
            )
            player.say("パンをてにいれた！")
        } else if (ランダムな数 == 8) {
            mobs.give(
            mobs.target(LOCAL_PLAYER),
            GOLDEN_APPLE,
            1
            )
            player.say("金のリンゴをてにいれた！")
        }
    }
}
let ランダムな数 = 0
let 開始位置: Position = null
let とびら = false
とびら = false

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、**白色の彩釉テラコッタ**の上に立ってランダムなアイテムがわたされているか確認しよう
つぎに、とびらの中に進んで**橙色の彩釉テラコッタ**の上に立ってランダムな場所に**空色の色付きガラス板**のかべができているか確認しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete1.gif">
<br></br>
できあがったのを確認したら、おくに進んでテレポートし、**村人に話しかけよう**
