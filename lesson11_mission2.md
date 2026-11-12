# エージェントのうごきをつくろう！

```blocks

player.onChat("agent", function () {
    while (スイッチ == true) {
        agent.teleport(world(player.position().getValue(Axis.X), 70, player.position().getValue(Axis.Z)), positions.toCompassDirection(player.getOrientation()))
    }
})
player.onItemInteracted(IRON_PICKAXE, function () {
    if (agent.inspect(AgentInspection.Block, FORWARD) == TNT) {
        player.say("TNTをこわしてしまった！")
        mobs.spawnParticle(EXPLOSION_HUGE, agent.getPosition())
        blocks.fill(
        AIR,
        positions.add(
        agent.getPosition(),
        pos(-1, 0, -1)
        ),
        positions.add(
        agent.getPosition(),
        pos(1, 0, 1)
        ),
        FillOperation.Replace
        )
    }
    agent.destroy(FORWARD)
    agent.collectAll()
})
function ランダムなブロックをおく (x: number, z: number) {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        ブロックのしゅるい = TNT
    } else if (ランダムな数 == 2) {
        ブロックのしゅるい = REDSTONE_ORE
    } else if (ランダムな数 == 3) {
        ブロックのしゅるい = EMERALD_ORE
    } else if (ランダムな数 == 4) {
        ブロックのしゅるい = GOLD_ORE
    } else if (ランダムな数 == 5) {
        ブロックのしゅるい = DIAMOND_ORE
    }
    blocks.place(ブロックのしゅるい, world(x, 70, z))
}
function しゅうりょう () {
    スイッチ = false
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    player.teleport(world(xのはじまり, 70, zのはじまり - 1))
    agent.teleport(world(315, 70, 81), WEST)
    agent.dropAll(DOWN)
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 30) {
            しゅうりょう()
        }
    }
})
player.onChat("run", function () {
    タイマー = 0
    player.say("こうせきをじゅんび中・・・")
    for (let z座標にたす数 = 0; z座標にたす数 <= 9; z座標にたす数++) {
        for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
            ランダムなブロックをおく(xのはじまり + x座標にたす数, zのはじまり + z座標にたす数)
        }
    }
    player.say("じゅんびかんりょう！")
    player.teleport(world(xのはじまり, 75, zのはじまり - 1))
    スイッチ = true
    player.runChatCommand("timer")
    player.runChatCommand("agent")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
})

let ブロックのしゅるい = 0
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
スイッチ = false
xのはじまり = 301
zのはじまり = 71
xのおわり = 310
zのおわり = 80
mobs.give(
mobs.target(LOCAL_PLAYER),
IRON_PICKAXE,
1
)

```

```template

function ランダムなブロックをおく (x: number, z: number) {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        ブロックのしゅるい = TNT
    } else if (ランダムな数 == 2) {
        ブロックのしゅるい = REDSTONE_ORE
    } else if (ランダムな数 == 3) {
        ブロックのしゅるい = EMERALD_ORE
    } else if (ランダムな数 == 4) {
        ブロックのしゅるい = GOLD_ORE
    } else if (ランダムな数 == 5) {
        ブロックのしゅるい = DIAMOND_ORE
    }
    blocks.place(ブロックのしゅるい, world(x, 70, z))
}
function しゅうりょう () {
    スイッチ = false
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 5) {
            しゅうりょう()
        }
    }
})
player.onChat("run", function () {
    タイマー = 0
    player.say("こうせきをじゅんび中・・・")
    for (let z座標にたす数 = 0; z座標にたす数 <= 9; z座標にたす数++) {
        for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
            ランダムなブロックをおく(xのはじまり + x座標にたす数, zのはじまり + z座標にたす数)
        }
    }
    player.say("じゅんびかんりょう！")
    スイッチ = true
    player.runChatCommand("timer")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
})

let ブロックのしゅるい = 0
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
スイッチ = false
xのはじまり = 301
zのはじまり = 71
xのおわり = 310
zのおわり = 80

```


## エージェントのうごきをつくろう！ @unplugged
エージェントがプレイヤーとおなじいちにうごいて、ブロックをこわすしくみをつくろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete2.gif">



## 目標(もくひょう)
Mission1では、ブロックをならべるしくみをつくりました
今度は、エージェントがうごいてブロックをこわすしくみをつくりましょう！
・ランダムにブロックをならべ終わったときとゲームしゅうりょうのときに、**プレイヤーをテレポート**させる
・ゲーム中、**プレイヤーの真下に、プレイヤーと同じ向きにエージェントがうごく**ようにする
・プレイヤーに**鉄のツルハシ**をわたし、**鉄のツルハシをつかうとエージェントが前の鉱石をこわして、アイテムをひろう**ようにする
・ゲームのおわりに、次のゲームのじゅんびのために、**エージェントをマグマのうえにテレポートさせてアイテムをすべてすてさせる**
それぞれ、どうすればできそうかかんがえよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete2.gif">



## プレイヤーをテレポートさせる
まずは、プレイヤーがテレポートするように、下のヒントをさんこうに**自分で考えてプログラミング**しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_teleport.gif">
・鉱石がならんだあとに、プレイヤーをテレポートさせる
・岩盤がならんだあとに、プレイヤーをテレポートさせる
・ゲームがスタートしたときは、x座標は``||variables.xのはじまり||``、y座標は**75**、z座標は``||variables.zのはじまり||``**から1ブロック北**にテレポートする
・ゲームがおわるときは、x座標は``||variables.xのはじまり||``、y座標は**70**、y座標は``||variables.zのはじまり||``**から1ブロック北**にテレポートする

```blocks

player.onChat("run", function () {
    タイマー = 0
    player.say("こうせきをじゅんび中・・・")
    for (let z座標にたす数 = 0; z座標にたす数 <= 9; z座標にたす数++) {
        for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
            ランダムなブロックをおく(xのはじまり + x座標にたす数, zのはじまり + z座標にたす数)
        }
    }
    player.say("じゅんびかんりょう！")
    player.teleport(world(xのはじまり, 75, zのはじまり - 1))
    スイッチ = true
    player.runChatCommand("timer")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
})
function しゅうりょう () {
    スイッチ = false
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    player.teleport(world(xのはじまり, 70, zのはじまり - 1))
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
function ランダムなブロックをおく (x: number, z: number) {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        ブロックのしゅるい = TNT
    } else if (ランダムな数 == 2) {
        ブロックのしゅるい = REDSTONE_ORE
    } else if (ランダムな数 == 3) {
        ブロックのしゅるい = EMERALD_ORE
    } else if (ランダムな数 == 4) {
        ブロックのしゅるい = GOLD_ORE
    } else if (ランダムな数 == 5) {
        ブロックのしゅるい = DIAMOND_ORE
    }
    blocks.place(ブロックのしゅるい, world(x, 70, z))
}
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
スイッチ = false
let xのはじまり = 301
let zのはじまり = 71
xのおわり = 310
zのおわり = 80

```



## エージェントをうごかすしくみ
エージェントをうごかすしくみについてかんがえよう！
・ゲーム中はずっとくりかえすために、``||variables.スイッチ||``が**真**のときループするようにする
・プレイヤーと同じ位置にエージェントがテレポートするための座標は、下のようになる
・x座標: **プレイヤーの位置のx座標**
・y座標: ブロックがある高さの**70**
・z座標: **プレイヤーの位置のz座標**
・向き: プレイヤーの向いている方向と同じ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_sync.gif">



## エージェントがうごくしくみをつくる
先ほどのかんがえをもとにして、エージェントがうごくしくみを**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドagentを入力した時||``の中にプログラムする
・ゲーム中はずっとくりかえすために、``||variables.スイッチ||``が**真**のときループするようにする
・プレイヤーと同じ位置にエージェントがテレポートするための座標は、下のようになる
・x座標: **プレイヤーの位置のx座標**
・y座標: ブロックがある高さの**70**
・z座標: **プレイヤーの位置のz座標**
・プレイヤーのx座標やz座標は、``||positions.ポジション||``にある``||positions.positionのx座標||``と、``||player.プレイヤー||``にある``||player.プレイヤーの位置||``をくみあわせる
・プレイヤーの向いている方向は、``||positions.ポジション||``にある``||positions.0の四方位||``と、``||player.プレイヤー||``にある``||player.プレイヤーの向いている方角||``をくみあわせる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_sync.gif">

```blocks

player.onChat("agent", function () {
    while (スイッチ == true) {
        agent.teleport(world(player.position().getValue(Axis.X), 70, player.position().getValue(Axis.Z)), positions.toCompassDirection(player.getOrientation()))
    }
})
let スイッチ = false
```



## 鉱石をこわす
プログラムを実行したときに、プレイヤーに**鉄のツルハシ**をわたし、**鉄のツルハシをつかうと、エージェントが前の鉱石をこわしてアイテムをひろう**ように、**自分で考えてプログラミング**しよう！
・``||blocks.～が(~0, ~0, ~0)に存在する||``と条件分岐をうまくくみあわせよう

```blocks

player.onItemInteracted(IRON_PICKAXE, function () {
    agent.destroy(FORWARD)
    agent.collectAll()
})
let ブロックのしゅるい = 0
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
スイッチ = false
xのはじまり = 301
zのはじまり = 71
xのおわり = 310
zのおわり = 80
mobs.give(
mobs.target(LOCAL_PLAYER),
IRON_PICKAXE,
1
)

```



## TNTをこわしたとき
ゲームをおもしろくするために、エージェントがTNTをこわしたときに、ばくはつしてエージェントのまわりのブロックが消えるようにしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_change_to_tnt.gif">
<br></br>
プレイヤーが鉄のツルハシを使ったときに、
・**huge_explosion**(だいばくはつ)という**パーティクル**(見た目の効果)を**エージェントの位置**に出す
・「TNTをこわしてしまった！」とメッセージ送信する
・エージェントのまわりのブロックを空気にする**
とすればよさそうです！




## プログラムを作る
エージェントがTNTをこわしてしまったときのうごきを、**自分で考えてプログラミング**しよう
プレイヤーが鉄のツルハシを使ったときに、
・**huge_explosion**(だいばくはつ)という**パーティクル**(見た目の効果)を**エージェントの位置**に出す
・「TNTをこわしてしまった！」とメッセージ送信する
・エージェントのまわりのブロックを空気にする**
・パーティクルは、``||mobs.モブ||``にある``||mobs.huge_explosionのパーティクルを(~0, ~0, ~0)に出す||``を使えば出すことができます
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_change_to_tnt.gif">

```blocks

player.onItemInteracted(IRON_PICKAXE, function () {
    if (agent.inspect(AgentInspection.Block, FORWARD) == TNT) {
        player.say("TNTをこわしてしまった！")
        mobs.spawnParticle(EXPLOSION_HUGE, agent.getPosition())
        blocks.fill(
        AIR,
        positions.add(
        agent.getPosition(),
        pos(-1, 0, -1)
        ),
        positions.add(
        agent.getPosition(),
        pos(1, 0, 1)
        ),
        FillOperation.Replace
        )
    }
    agent.destroy(FORWARD)
    agent.collectAll()
})

```



## エージェントにアイテムをすてさせる
次のMission3では、エージェントが拾ったアイテムによって得点をつけるようにしようを思います
エージェントがもちものを持ったままにしないように、``||functions.しゅうりょう||``を実行したときに、**エージェントのもちものをすべてマグマにすてさせる**よう、**自分で考えてプログラミング**しよう
・ワールド(315, 70, 81)にエージェントをテレポーさせて、すべてすてさせる

```blocks

function しゅうりょう () {
    スイッチ = false
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    player.teleport(world(xのはじまり, 70, zのはじまり - 1))
    agent.teleport(world(315, 70, 81), WEST)
    agent.dropAll(DOWN)
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}

```




## チャットでrunと入力したとき
チャットでrunと入力したときに、あたらしくつくったチャットコマンド**agent**も実行するように、**自分で考えてプログラミング**しよう！


```blocks

player.onChat("run", function () {
    タイマー = 0
    player.say("こうせきをじゅんび中・・・")
    for (let z座標にたす数 = 0; z座標にたす数 <= 9; z座標にたす数++) {
        for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
            ランダムなブロックをおく(xのはじまり + x座標にたす数, zのはじまり + z座標にたす数)
        }
    }
    player.say("じゅんびかんりょう！")
    player.teleport(world(xのはじまり, 75, zのはじまり - 1))
    スイッチ = true
    player.runChatCommand("timer")
    player.runChatCommand("agent")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
})
player.onChat("agent", function () {
    while (スイッチ == true) {
        agent.teleport(world(player.position().getValue(Axis.X), 70, player.position().getValue(Axis.Z)), positions.toCompassDirection(player.getOrientation()))
    }
})
player.onItemInteracted(IRON_PICKAXE, function () {
    if (agent.inspect(AgentInspection.Block, FORWARD) == TNT) {
        player.say("TNTをこわしてしまった！")
        mobs.spawnParticle(EXPLOSION_HUGE, agent.getPosition())
        blocks.fill(
        AIR,
        positions.add(
        agent.getPosition(),
        pos(-1, 0, -1)
        ),
        positions.add(
        agent.getPosition(),
        pos(1, 0, 1)
        ),
        FillOperation.Replace
        )
    }
    agent.destroy(FORWARD)
    agent.collectAll()
})
function ランダムなブロックをおく (x: number, z: number) {
    ランダムな数 = randint(1, 5)
    if (ランダムな数 == 1) {
        ブロックのしゅるい = TNT
    } else if (ランダムな数 == 2) {
        ブロックのしゅるい = REDSTONE_ORE
    } else if (ランダムな数 == 3) {
        ブロックのしゅるい = EMERALD_ORE
    } else if (ランダムな数 == 4) {
        ブロックのしゅるい = GOLD_ORE
    } else if (ランダムな数 == 5) {
        ブロックのしゅるい = DIAMOND_ORE
    }
    blocks.place(ブロックのしゅるい, world(x, 70, z))
}
function しゅうりょう () {
    スイッチ = false
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    player.teleport(world(xのはじまり, 70, zのはじまり - 1))
    agent.teleport(world(315, 70, 81), WEST)
    agent.dropAll(DOWN)
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 30) {
            しゅうりょう()
        }
    }
})
let ブロックのしゅるい = 0
let ランダムな数 = 0
let タイマー = 0
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
スイッチ = false
xのはじまり = 301
zのはじまり = 71
xのおわり = 310
zのおわり = 80
mobs.give(
mobs.target(LOCAL_PLAYER),
IRON_PICKAXE,
1
)

```



## 実行しよう！
プログラムが完成したら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
ゲーム画面にもどったら、チャットで**run**と入力して、ゲームをスタートしよう
スタートしたら、移動してエージェントをうごかし、鉄のツルハシをつかって鉱石をほってみよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete2.gif">
<br></br>
タイマーは約**30秒**に設定しているので、じっさいにゲームをやってみたら、**村人に話しかけよう**
