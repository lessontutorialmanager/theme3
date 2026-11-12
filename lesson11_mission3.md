# ゲームをかんせいさせよう！

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
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "けっか：" + ポイント + "ポイント")
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
function ポイントをしゅうけいする (スロット番号: number) {
    if (agent.getItemDetail(スロット番号) == TNT) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += -1
        }
    } else if (agent.getItemDetail(スロット番号) == REDSTONE) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 1
        }
    } else if (agent.getItemDetail(スロット番号) == EMERALD) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 3
        }
    } else if (agent.getItemDetail(スロット番号) == RAW_GOLD) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 5
        }
    } else if (agent.getItemDetail(スロット番号) == DIAMOND) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 10
        }
    }
}
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 30) {
            for (let カウンター = 0; カウンター <= 26; カウンター++) {
                ポイントをしゅうけいする(カウンター + 1)
            }
            しゅうりょう()
        }
    }
})
player.onChat("run", function () {
    タイマー = 0
    ポイント = 0
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
    player.runChatCommand("change")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
})
player.onChat("change", function () {
    while (スイッチ == true) {
        ランダムなx座標 = randint(xのはじまり, xのおわり)
        ランダムなz座標 = randint(zのはじまり, zのおわり)
        if (!(blocks.testForBlock(AIR, world(ランダムなx座標, 70, ランダムなz座標)))) {
            ランダムなブロックをおく(ランダムなx座標, ランダムなz座標)
            loops.pause(2000)
        }
    }
})
let ランダムなz座標 = 0
let ランダムなx座標 = 0
let タイマー = 0
let ブロックのしゅるい = 0
let ランダムな数 = 0
let ポイント = 0
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
let スイッチ = false
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
    player.runChatCommand("make")
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


## ゲームをかんせいさせよう！@unplugged
ポイントのしくみや、ランダムにブロックのしゅるいをかえるしくみをつくって、ゲームをかんせいさせよう
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete3.gif">



## 目標(もくひょう)
ゲームをかんせいさせよう！
・変数``||variables.ポイント||``をつくり、時間がきたら、エージェントのもちものによってポイントを計算してタイトルを表示する
・ゲーム中に、ランダムな場所のブロックの種類をかえる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete3.gif">



## エージェントのもちものをしらべる
エージェントもプレイヤーと同じように、もちものリストがあります
エージェントのもちものリストは、1番～27番まであり、どの番号に何のアイテムやブロックを持っているかは、``||agent.エージェント||``にある``||agent.エージェントのスロット番号1のアイテム||``でしらべることができます
また、``||agent.エージェントのスロット番号1のアイテムの数||``をつかえば、その番号のアイテムをいくつ持っているかかくにんすることができます
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_agent_slot.png">
今回は、引数**スロット番号**を持った関数``||functions.ポイントをしゅうけいする||``を作って、エージェントのもちものリストを1番から27番まで、何を持っているかかくにんして、そのアイテムによってポイントがつくようにしましょう！



## 関数と変数をつくる
じゅんびとして、引数**スロット番号**を持った関数``||functions.ポイントをしゅうけいする||``と、ポイントを入れる変数``||variables.ポイント||``を作ろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_make_function_count.gif">



## ポイントをしゅうけいする
作った関数``||functions.ポイントをしゅうけいする||``の中に、スロット番号のブロックやアイテムによって``||variables.ポイント||``の数字を変えるよう、**自分で考えてプログラミング**しよう！
・ブロックが**TNT**のとき: ブロック1つにつきポイントを**-1**する
・アイテムが**レッドストーンダスト**のとき: ブロック1つにつきポイントを**1**ふやす
・アイテムが**エメラルド**のとき: ブロック1つにつきポイントを**3**ふやす
・アイテムが**金の原石**のとき: ブロック1つにつきポイントを**5**ふやす
・アイテムが**ダイヤモンド**のとき: ブロック1つにつきポイントを**10**ふやす
・``||agent.エージェントのスロット番号1のアイテムの数||``をつかって、それぞれのブロックやアイテムをもっている数だけ``||variables.ポイント||``の数字を変える

![check_slot](https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_check_slot.gif)



## しゅうけいけっかを表示する
``||variables.ポイント||``のけっかを、``||functions.しゅうりょう||``の中のタイトルで表示しよう！
・``||gameplay.～にタイトル しゅうりょう！ を表示する||``の**サブタイトル**に、**けっか：～ポイント**と表示されるようにする
・文字と``||variables.ポイント||``をくみあわせるには、``||texts.文字列をつなげる||``をつかう

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
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "けっか：" + ポイント + "ポイント")
}
let ポイント = 0
let スイッチ = false
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0

```



## 関数を呼び出す
指定した番号のエージェントのもちものリストのポイントを調べる関数``||functions.ポイントをしゅうけいする||``と、けっかをタイトルで表示するしくみは作り終わりました
しかし、まだ``||functions.ポイントをしゅうけいする||``**を呼び出すしくみ**をつくってません！
つくった``||functions.ポイントをしゅうけいする||``を、せいげんじかんがきたときに、もちものリストの1番～27番まで呼び出そう！
・``||loops.変数 カウンターを0～4に変えてくりかえす||``を使う
・1番から27番までくりかえし``||functions.ポイントをしゅうけいする||``でかくにんできるように、引数に``||variables.カウンター||``**+ 1**をはめこむ
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_counter.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_call_function.gif">

```blocks

function ポイントをしゅうけいする (スロット番号: number) {
    if (agent.getItemDetail(スロット番号) == TNT) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += -1
        }
    } else if (agent.getItemDetail(スロット番号) == REDSTONE) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 1
        }
    } else if (agent.getItemDetail(スロット番号) == EMERALD) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 3
        }
    } else if (agent.getItemDetail(スロット番号) == RAW_GOLD) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 5
        }
    } else if (agent.getItemDetail(スロット番号) == DIAMOND) {
        for (let index = 0; index < agent.getItemCount(スロット番号); index++) {
            ポイント += 10
        }
    }
}
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 30) {
            for (let カウンター = 0; カウンター <= 26; カウンター++) {
                ポイントをしゅうけいする(カウンター + 1)
            }
            しゅうりょう()
        }
    }
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
    agent.teleport(world(315, 70, 81), WEST)
    agent.dropAll(DOWN)
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "けっか：" + ポイント + "ポイント")
}
let xのはじまり = 0
let zのはじまり = 0
let xのおわり = 0
let zのおわり = 0
let タイマー = 0
let ポイント = 0
let スイッチ = false

```



## ランダムな場所のブロックをかえるしくみをかんがえる
つぎに、**ゲーム中に、2秒に1回、ランダムな場所のブロックがかわっていくしくみ**をかんがえよう！
・``||varibales.スイッチ||``をつかって、**ゲームがはじまっている間だけくりかえす**
・変数``||variables.ランダムなx座標||``、``||variables.ランダムなz座標||``をつくって、**ブロックがならんでいるはんい内のランダムな座標をえらぶ**
・**条件分岐**で、**えらんだ場所にもしブロックがある**なら``||functions.ランダムなブロックをおく||``を呼び出して、**ブロックのしゅるいをランダムに変える**
(えらんだ場所にブロックが**ある** = えらんだ場所が**空気ブロックじゃない**)
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_random_change.gif">



## 変数をつくる
しくみをつくるじゅんびとして、変数``||variables.ランダムなx座標||``、``||variables.ランダムなz座標||``をつくろう！



## ランダムな座標をえらぶ
変数``||variables.ランダムなx座標||``、``||variables.ランダムなz座標||``には、**はんい内のランダムな座標**を入れたいと思います
x座標、z座標のはんいの数字は、``||variables.xのはじまり||``、``||variables.zのはじまり||``、``||variables.xのおわり||``、``||variables.zのおわり||``にはいっています
このことをつかって、``||variables.ランダムなx座標||``、``||variables.ランダムなz座標||``に**はんい内のランダムな座標**を入れるよう、**自分で考えてプログラミング**しよう！
・プログラムは、``||player.チャットコマンドchangeを入力した時||``の中につくる



## ブロックをかえるしくみをつくる
さきほどのかんがえをもとにして、``||player.チャットコマンドchangeを入力した時||``の中に**ゲーム中に、2秒に1回、ランダムな場所のブロックがかわっていくしくみ**を**自分で考えてプログラミング**しよう！
・``||variables.スイッチ||``が**真**のとき、くりかえすようにする
・``||variables.ランダムなx座標||``、``||variables.ランダムなz座標||``でえらんだ場所のブロックが、**空気ブロックでない**なら、関数``||functions.ランダムなブロックをおく||``を呼び出す
・y座標は**70**にする
・空気ブロックでないことをしらべるには、``||blocks.ブロック||``にある``||blocks.～が(~0, ~0, ~0)に存在する||``と、``||logics.論理||``にある``||logics.ではない||``をくみあわせる
・2秒に1回変えるために、``||loops.2000ミリ秒まつ||``をつかう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_random_change.gif">

```blocks

player.onChat("change", function () {
    while (スイッチ == true) {
        ランダムなx座標 = randint(xのはじまり, xのおわり)
        ランダムなz座標 = randint(zのはじまり, zのおわり)
        if (!(blocks.testForBlock(AIR, world(ランダムなx座標, 70, ランダムなz座標)))) {
            ランダムなブロックをおく(ランダムなx座標, ランダムなz座標)
            loops.pause(2000)
        }
    }
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
let ランダムなz座標 = 0
let ランダムなx座標 = 0
let ブロックのしゅるい = 0
let ランダムな数 = 0
let zのおわり = 0
let xのおわり = 0
let zのはじまり = 0
let xのはじまり = 0
let スイッチ = false

```



## チャットでrunと入力したとき
さいごに、前回のミッションでつくった``||player.チャットコマンドrunを入力した時||``に、プログラムをついかしよう！
・あたらしくつくったチャットコマンド**change**を実行するようにする

```blocks

player.onChat("run", function () {
    タイマー = 0
    ポイント = 0
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
    player.runChatCommand("change")
    gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "たくさんほろう！")
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
let タイマー = 0
let ポイント = 0
let スイッチ = false

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで**run**と入力して、**ゲームにちょうせんしよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete3.gif">
<br></br>
ゲームが終わったら、**村人に話しかけよう**
