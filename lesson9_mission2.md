# ランダムなモンスターをスポーンさせよう！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            たおした数 = 0
            blocks.fill(
            AIR,
            world(79, 49, 109),
            world(87, 50, 116),
            FillOperation.Replace
            )
            とびらをあける()
            ランダムなアイテムをわたす()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            かべをつくる()
            ランダムなモンスターをスポーンさせる()
            とびら = false
        }
    }
})
player.onDied(function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "しんでしまった・・・", "たおした数　" + たおした数)
    mobs.kill(
    mobs.entitiesByType(mobs.monster(WITHER_SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(ZOMBIE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(BLAZE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(RAVAGER))
    )
    gameplay.setDifficulty(PEACEFUL)
    player.teleport(world(83, 63, 81))
})
mobs.onMobKilled(mobs.monster(WITHER_SKELETON), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(SKELETON), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(BLAZE), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(RAVAGER), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
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
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    gameplay.setDifficulty(NORMAL)
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
function ランダムなモンスターをスポーンさせる () {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
        player.say("ウィザースケルトンだ！")
    } else if (ランダムな数 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), world(83, 49, 118))
        player.say("ゾンビだ！")
    } else if (ランダムな数 == 3) {
        mobs.spawn(mobs.monster(SKELETON), world(83, 49, 118))
        player.say("スケルトンだ！")
    } else if (ランダムな数 == 4) {
        mobs.spawn(mobs.monster(BLAZE), world(83, 49, 118))
        player.say("ブレイズだ！")
    } else if (ランダムな数 == 5) {
        mobs.spawn(mobs.monster(RAVAGER), world(83, 49, 118))
        player.say("ラヴェジャーだ！")
    }
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
            3
            )
            player.say("金のリンゴをてにいれた！")
        }
    }
}
let ランダムな数 = 0
let 開始位置: Position = null
let たおした数 = 0
let とびら = false
とびら = false
たおした数 = 0

```

```template

player.onDied(function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "しんでしまった・・・", "")
    mobs.kill(
    mobs.entitiesByType(mobs.monster(WITHER_SKELETON))
    )
    gameplay.setDifficulty(PEACEFUL)
    player.teleport(world(83, 63, 81))
})
mobs.onMobKilled(mobs.monster(WITHER_SKELETON), function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
    gameplay.setDifficulty(PEACEFUL)
    player.teleport(world(83, 63, 81))
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
    gameplay.setDifficulty(NORMAL)
    mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
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
            3
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


## ランダムなモンスターをスポーンさせよう！ @unplugged
ランダムなモンスター3体とたたかえるようにしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete2.gif">



## 目標(もくひょう)
プログラムを改造して、ランダムなモンスターとれんぞくでたたかえるようにしよう！
また、クリアできなかったときに、何体たおすことができたのか、タイトルで表示できるようにしよう
・``||functions.ランダムなモンスターをスポーンさせる||``という関数をつくって、**橙色の彩釉テラコッタ**の上に立ったときに、**ウィザースケルトン**、**ゾンビ**、**スケルトン**、**ブレイズ**、**ラヴェジャー**のなかからランダムなモンスターをスポーンさせる
・``||variables.たおした数||``という変数を用意して、たおした数が**3**になったらクリア、それ以外のときは``||functions.ランダムなモンスターをスポーンさせる||``を呼び出して、次のモンスターをスポーンさせる
・プレイヤーがモンスターを3体たおす前にしんでしまったとき、タイトルで何体たおせたか表示する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete2.gif">



## ランダムなモンスターをスポーンさせる
ランダムなモンスターをスポーンさせる方法を考えよう！
スポーンさせたいモンスターは**5種類**なので、前回のレッスンで作った``||variables.ランダムな数||``に**1～5までのランダムな数**を入れて、条件分岐すればよさそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_flow2.png">



## 関数を作る
まずは準備として、``||functions.ランダムなモンスターをスポーンさせる||``を作成しよう！

```blocks

function ランダムなモンスターをスポーンさせる () {
}

```



## 条件分岐を考える
``||variables.ランダムな数||``に**1～5のランダムな数**を入れ、その数によってランダムなモンスターがスポーンする条件分岐を、**自分で考えてプログラミング**しよう！
・``||positions.ワールド(83, 49, 118)||``にモンスターをスポーンさせる
・``||variables.ランダムな数||``が**1**: **ウィザースケルト**ンをスポーン
・``||variables.ランダムな数||``が**2**: **ゾンビ**をスポーン
・``||variables.ランダムな数||``が**3**: **スケルトン**をスポーン
・``||variables.ランダムな数||``が**4**: **ブレイズ**をスポーン
・``||variables.ランダムな数||``が**5**: **ラヴェジャー**をスポーン
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_flow2.png">
・条件分岐の最後が「でなければ」になっているときは、⊕をおしたあとに⊖をおすと、「でなければもし」に変わります！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_elseif.gif">




## メッセージ送信する
それぞれのモンスターがスポーンするときに、「ウィザースケルトンだ！」のように**メッセージ送信**するよう、**自分で考えてプログラミング**しよう！

```blocks

function ランダムなモンスターをスポーンさせる () {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
        player.say("ウィザースケルトンだ！")
    } else if (ランダムな数 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), world(83, 49, 118))
        player.say("ゾンビだ！")
    } else if (ランダムな数 == 3) {
        mobs.spawn(mobs.monster(SKELETON), world(83, 49, 118))
        player.say("スケルトンだ！")
    } else if (ランダムな数 == 4) {
        mobs.spawn(mobs.monster(BLAZE), world(83, 49, 118))
        player.say("ブレイズだ！")
    } else if (ランダムな数 == 5) {
        mobs.spawn(mobs.monster(RAVAGER), world(83, 49, 118))
        player.say("ラヴェジャーだ！")
    }
}

```




## プログラムを修正する
前回作ったプログラムでは、``||functions.とびらをしめる||``の中にウィザースケルトンをスポーンさせるプログラムを入れていました
プログラムを修正しましょう！
・``||functions.とびらをしめる||``の中の、ウィザースケルトンをスポーンさせるプログラムを消す
・橙色の彩釉テラコッタの上に立ったときに、``||functions.ランダムなモンスターをスポーンさせる||``を呼び出すようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_call_function2.gif">
これで、ゲームをはじめたときに、ランダムなモンスターをスポーンさせるプログラムが完成しました！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == false) {
            blocks.fill(
            AIR,
            world(79, 49, 109),
            world(87, 50, 116),
            FillOperation.Replace
            )
            とびらをあける()
            ランダムなアイテムをわたす()
            とびら = true
        }
    }
    if (blocks.testForBlock(ORANGE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        if (とびら == true) {
            とびらをしめる()
            かべをつくる()
            ランダムなモンスターをスポーンさせる()
            とびら = false
        }
    }
})
function ランダムなモンスターをスポーンさせる () {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
        player.say("ウィザースケルトンだ！")
    } else if (ランダムな数 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), world(83, 49, 118))
        player.say("ゾンビだ！")
    } else if (ランダムな数 == 3) {
        mobs.spawn(mobs.monster(SKELETON), world(83, 49, 118))
        player.say("スケルトンだ！")
    } else if (ランダムな数 == 4) {
        mobs.spawn(mobs.monster(BLAZE), world(83, 49, 118))
        player.say("ブレイズだ！")
    } else if (ランダムな数 == 5) {
        mobs.spawn(mobs.monster(RAVAGER), world(83, 49, 118))
        player.say("ラヴェジャーだ！")
    }
}
function とびらをあける () {
    blocks.fill(
    AIR,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
}
function とびらをしめる () {
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(82, 49, 106),
    world(84, 51, 106),
    FillOperation.Replace
    )
    gameplay.setDifficulty(NORMAL)
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
            3
            )
            player.say("金のリンゴをてにいれた！")
        }
    }
}

```



## モンスターをたおした時を考える
つぎに、モンスターをたおした時、ゲームがどのように進めばよいか考えてみましょう
下の図のようにゲームが進めばよさそうです！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_on_killed.png">




## プログラムを修正する
前回作った、ウィザースケルトンをたおしたときのプログラムを見てみましょう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_unfixed.png">
前回は、**1体たおせばクリア**だったので、たおしたら「クリア！」とタイトルを表示して、プレイヤーをテレポートさせていました
今回は、**3体たおせばクリア**となり、**3体たおしていない場合は、ランダムなモンスターをスポーンさせる**必要があります
``|||variables.たおした数||``という変数を作って、**3体たおしたかどうかで条件分岐**するように、**自分で考えてプログラミングを修正**しよう！
・モンスターをたおしたとき、``||variables.たおした数||``を**1**増やす
・たおした数によって、前回作ったクリアの時のプログラムを実行するのか、``||functions.ランダムなモンスターをスポーンさせる||``を呼び出すのか条件分岐する



## メッセージ送信する
``||functions.ランダムなモンスターをスポーンさせる||``を呼び出す前に、「次のモンスターは・・・」とメッセージ送信しよう！

```blocks

mobs.onMobKilled(mobs.monster(WITHER_SKELETON), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
function ランダムなモンスターをスポーンさせる () {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
        player.say("ウィザースケルトンだ！")
    } else if (ランダムな数 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), world(83, 49, 118))
        player.say("ゾンビだ！")
    } else if (ランダムな数 == 3) {
        mobs.spawn(mobs.monster(SKELETON), world(83, 49, 118))
        player.say("スケルトンだ！")
    } else if (ランダムな数 == 4) {
        mobs.spawn(mobs.monster(BLAZE), world(83, 49, 118))
        player.say("ブレイズだ！")
    } else if (ランダムな数 == 5) {
        mobs.spawn(mobs.monster(RAVAGER), world(83, 49, 118))
        player.say("ラヴェジャーだ！")
    }
}

```



## プログラムをコピーする
これで、ウィザースケルトンをたおしたときに、``||variables.たおした数||``が3ならクリア、そうでないなら次のモンスター出すプログラムができました
ほかのモンスターをたおしたときも、同じようにゲームが進む必要があります
作ったプログラムを**右クリッ**ク(タブレットなどの場合は**長タップ**)して、「複製(ふくせい)する」をおし、プログラムをコピーしよう！
コピーしたら、たおしたモンスターを**ゾンビ**にしよう
同じように、**スケルトン**、**ブレイズ**、**ラヴェジャー**をたおしたときのプログラムも作ろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_duplicate.gif">

```blocks

mobs.onMobKilled(mobs.monster(WITHER_SKELETON), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(SKELETON), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(BLAZE), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
mobs.onMobKilled(mobs.monster(RAVAGER), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        player.say("次のモンスターは・・・")
        ランダムなモンスターをスポーンさせる()
    }
})
function ランダムなモンスターをスポーンさせる () {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        mobs.spawn(mobs.monster(WITHER_SKELETON), world(83, 49, 118))
        player.say("ウィザースケルトンだ！")
    } else if (ランダムな数 == 2) {
        mobs.spawn(mobs.monster(ZOMBIE), world(83, 49, 118))
        player.say("ゾンビだ！")
    } else if (ランダムな数 == 3) {
        mobs.spawn(mobs.monster(SKELETON), world(83, 49, 118))
        player.say("スケルトンだ！")
    } else if (ランダムな数 == 4) {
        mobs.spawn(mobs.monster(BLAZE), world(83, 49, 118))
        player.say("ブレイズだ！")
    } else if (ランダムな数 == 5) {
        mobs.spawn(mobs.monster(RAVAGER), world(83, 49, 118))
        player.say("ラヴェジャーだ！")
    }
}

```



## たおした数をリセットする
ゲームをはじめるときに、``||variables.たおした数||``をリセットするようにしよう！
・**白色の彩釉テラコッタ**の上に立ったときのプログラムに、``||variables.変数 たおした数 を0にする||``をはめこむ



## プレイヤーが死んだとき
前回作ったプログラムでは、プレイヤーが死んだとき、ステージ内のウィザースケルトンをたおして、タイトルを表示し、プレイヤーをテレポートするようにしました
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_on_died.png">
まずは、ウィザースケルトン以外のゾンビ、スケルトン、ブレイズ、ラヴェジャーもたおすようにプログラムを修正しよう！

```blocks

player.onDied(function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "しんでしまった・・・", "")
    mobs.kill(
    mobs.entitiesByType(mobs.monster(WITHER_SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(ZOMBIE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(BLAZE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(RAVAGER))
    )
    gameplay.setDifficulty(PEACEFUL)
    player.teleport(world(83, 63, 81))
})

```




## たおした数を表示する
つぎに、つくった``||variables.たおした数||``をつかって、サブタイトルに「たおした数　○」と表示するようにしよう！
・``||text.文字列||``から、``||text.文字列をつなげる||``を取り出して、``||gameplay.すべてのプレーヤー(@a)にタイトル 死んでしまった・・・||``の**サブタイトル**の部分にはめ込む
・``||text.文字列をつなげる||``の左側に、「たおした数　」と入力し、右側に``||variables.たおした数||``をはめ込む
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_concatenate.gif">

```blocks

player.onDied(function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "しんでしまった・・・", "たおした数　" + たおした数)
    mobs.kill(
    mobs.entitiesByType(mobs.monster(WITHER_SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(ZOMBIE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(SKELETON))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(BLAZE))
    )
    mobs.kill(
    mobs.entitiesByType(mobs.monster(RAVAGER))
    )
    gameplay.setDifficulty(PEACEFUL)
    player.teleport(world(83, 63, 81))
})

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、**白の彩釉テラコッタ**の上に立ってランダムなアイテムをうけとって中に入り、**橙色の彩釉テラコッタ**の上に立ってランダムなモンスターをスポーンさせてたたかおう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_complete2.gif">
<br></br>
何回かたたかって、ランダムなモンスターがスポーンしているのを確認したら、**村人に話しかけよう**
