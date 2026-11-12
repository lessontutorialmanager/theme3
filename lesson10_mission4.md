# ゲームをさらに面白くしよう！



```template

player.onChat("run", function () {
    gameplay.title(mobs.target(ALL_PLAYERS), "よーい・・・", "")
    loops.pause(2000)
    gameplay.title(mobs.target(ALL_PLAYERS), "スタート！", "")
    タイマー = 0
    スイッチ = true
    loops.pause(100)
    player.runChatCommand("jump")
    player.runChatCommand("effect")
    player.runChatCommand("timer")
    player.runChatCommand("goal")
})
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
    }
})
player.onChat("goal", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(BLUE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
            gameplay.title(mobs.target(ALL_PLAYERS), "ゴール！", "" + "きろく　" + タイマー + "びょう")
            タイマー = 0
            スイッチ = false
        }
    }
})
player.onChat("jump", function () {
    while (スイッチ) {
        while (blocks.testForBlock(DIAMOND_BLOCK, pos(0, -1, 0))) {
            mobs.applyEffect(LEVITATION, mobs.target(ALL_ENTITIES), 1, 2)
        }
    }
})
player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
        }
    }
})
function とくしゅこうか () {
    ランダムな数 = randint(1, 4)
    if (ランダムな数 == 1) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 2) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 3) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードダウン・・・")
    } else if (ランダムな数 == 4) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードダウン・・・")
    }
}
player.onChat("make", function () {
    blocks.fill(
    BLUE_GLAZED_TERRACOTTA,
    world(157, 66, -24),
    world(158, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    blocks.blockWithData(OAK_FENCE_GATE, 1),
    world(160, 66, -24),
    world(160, 66, -20),
    FillOperation.Replace
    )
    blocks.fill(
    STONE_PRESSURE_PLATE,
    world(159, 67, -24),
    world(159, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    GRAY_CARPET,
    world(160, 67, -24),
    world(160, 67, -20),
    FillOperation.Replace
    )
    blocks.fill(
    LIGHT_BLUE_STAINED_GLASS,
    world(160, 69, -25),
    world(160, 69, -19),
    FillOperation.Replace
    )
})
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
スイッチ = false

```

```template

player.onChat("run", function () {
    スイッチ = true
    player.runChatCommand("jump")
    player.runChatCommand("effect")
})
player.onChat("jump", function () {
    while (スイッチ) {
        while (blocks.testForBlock(DIAMOND_BLOCK, pos(0, -1, 0))) {
            mobs.applyEffect(LEVITATION, mobs.target(ALL_ENTITIES), 1, 5)
        }
    }
})
player.onChat("effect", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(REDSTONE_BLOCK, pos(0, -1, 0))) {
            とくしゅこうか()
        }
    }
})
function とくしゅこうか () {
    ランダムな数 = randint(1, 4)
    if (ランダムな数 == 1) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 2) {
        mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードアップ！")
    } else if (ランダムな数 == 3) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 3)
        player.say("スピードダウン・・・")
    } else if (ランダムな数 == 4) {
        mobs.applyEffect(SLOWNESS, mobs.target(LOCAL_PLAYER), 2, 5)
        player.say("スピードダウン・・・")
    }
}
player.onChat("make", function () {})
player.onChat("timer", function () {})
player.onChat("goal", function () {})
let ランダムな数 = 0
let スイッチ = false
スイッチ = false


```

## ゲームをさらに面白くしよう！@unplugged
工夫(くふう)してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例①
マグマや氷などのしょうがいぶつをコースにおいて、レースをおもしろくしよう！



## 例➁
コースをもっとながくして、オリジナルのコースをつくってみよう！
