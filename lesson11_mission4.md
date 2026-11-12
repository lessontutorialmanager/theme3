# ゲームをさらに面白くしよう！



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

## ゲームをさらに面白くしよう！@unplugged
工夫(くふう)してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例①
とうじょうする鉱石(こうせき)のしゅるいをふやして、もらえるポイントをかえてみよう！
また、ゲーム中にブロックの種類がかわるスピードをかえてみよう



## 例➁
エージェントが自動で鉱石をほるようにプログラミングしよう！

```blocks

player.onItemInteracted(NETHERITE_PICKAXE, function () {
    チェック = true
    while (チェック == true) {
        if (agent.inspect(AgentInspection.Block, FORWARD) != AIR && agent.inspect(AgentInspection.Block, FORWARD) != TNT) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(FORWARD, 1)
        } else if (agent.inspect(AgentInspection.Block, LEFT) != AIR && agent.inspect(AgentInspection.Block, LEFT) != TNT) {
            agent.turn(LEFT_TURN)
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(FORWARD, 1)
        } else if (agent.inspect(AgentInspection.Block, RIGHT) != AIR && agent.inspect(AgentInspection.Block, RIGHT) != TNT) {
            agent.turn(RIGHT_TURN)
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(FORWARD, 1)
        } else {
            チェック = false
        }
    }
})
let チェック = false

```
