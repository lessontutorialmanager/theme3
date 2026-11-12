# ゲームをさらに面白くしよう！



```template

player.onDied(function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "しんでしまった・・・", "" + "たおした数　" + たおした数)
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
}
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
    if (blocks.testForBlock(BEDROCK, pos(0, -1, 0))) {
        if (とびら == false) {
            loops.pause(3000)
            カミナリを落とす()
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
function カミナリを落とす () {
    くじ = randint(1, 2)
    if (くじ == 1) {
        for (let index = 0; index < 3; index++) {
            開始位置 = randpos(
            world(79, 48, 109),
            world(87, 48, 117)
            )
            blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
            player.say("カミナリだ！")
            loops.pause(1000)
            mobs.spawn(LIGHTNING_BOLT, 開始位置)
            blocks.place(BEDROCK, 開始位置)
        }
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
let くじ = 0
let ランダムな数 = 0
let 開始位置: Position = world(0, 0, 0)
let たおした数 = 0
let とびら = false
とびら = false
たおした数 = 0


```

## ゲームをさらに面白くしよう！@unplugged
工夫(くふう)してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例①
スポーンするモンスターの種類をふやしてみよう！



## 例➁
モンスターをたおしたときに、プレイヤーに特殊効果(とくしゅこうか)を与えるようにしよう！

```blocks

mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    たおした数 += 1
    if (たおした数 == 3) {
        gameplay.title(mobs.target(ALL_PLAYERS), "クリア！！", "")
        gameplay.setDifficulty(PEACEFUL)
        player.teleport(world(83, 63, 81))
    } else {
        mobs.applyEffect(STRENGTH, mobs.target(LOCAL_PLAYER), 300, 10)
        player.say("こうげきりょくがあがった！")
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


## 例③
倒(たお)したときに出てくるモンスターの数を増(ふ)やそう！
``||mobs.モンスターが死んだ時||``を使って、ウィザースケルトンをたおすとラヴェジャーがスポーンするようにして、ラヴェジャーをたおしたらクリアとなるようにしよう！

```blocks

function TNTを出す () {
    if (player.position() == TNTの場所) {
        player.say("TNTだ！！")
        mobs.spawn(PRIMED_TNT, pos(0, 0, 0))
    }
}
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
            TNTの場所 = randpos(
            world(79, 49, 109),
            world(87, 49, 116)
            )
        }
    }
    if (blocks.testForBlock(BEDROCK, pos(0, -1, 0))) {
        if (とびら == false) {
            loops.pause(3000)
            カミナリを落とす()
        }
        if (とびら == false) {
            TNTを出す()
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
function カミナリを落とす () {
    くじ = randint(1, 2)
    if (くじ == 1) {
        for (let index = 0; index < 3; index++) {
            開始位置 = randpos(
            world(79, 48, 109),
            world(87, 48, 117)
            )
            blocks.place(YELLOW_GLAZED_TERRACOTTA, 開始位置)
            player.say("カミナリだ！")
            loops.pause(1000)
            mobs.spawn(LIGHTNING_BOLT, 開始位置)
            blocks.place(BEDROCK, 開始位置)
        }
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
let くじ = 0
let ランダムな数 = 0
let TNTの場所: Position = null
let たおした数 = 0
let とびら = false
let 開始位置: Position = null
開始位置 = world(0, 0, 0)
とびら = false
たおした数 = 0
TNTの場所 = world(0, 0, 0)


```
