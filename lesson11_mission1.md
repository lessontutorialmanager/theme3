# ゲームのきほんのながれをつくろう！

```blocks

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

```template

player.onChat("timer", function () {})
player.onChat("run", function () {})

```


## ゲームのきほんのながれをつくろう！ @unplugged
ゲームのはじまりからおわりまでのながれをつくろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete1.gif">



## 目標(もくひょう)
ゲームのきほんのながれをつくろう！
・チャットで**run**と入力すると、**はんいにランダムな鉱石のブロックがならび**、「スタート！」と**タイトルを表示する**
・制限時間(せいげんじかん)がたつと、「しゅうりょう！」と**タイトルを表示**して、**はんいのブロックを全て岩盤(がんばん)にする**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete1.gif">
それぞれ、**チャットコマンド**や**関数**を使ってつくっていこう！



## ランダムにブロックをえらんで置くしくみを考える
まずは、指定した座標に、ランダムなブロックを置く``||functions.関数||``のしくみをかんがえてみよう！
・変数``||variables.ランダムな数||``に1から5のランダムな数を入れる
・**条件分岐**をつかって、``||variables.ランダムな数||``にはいった数によって、変数``||variables.ブロックのしゅるい||``にブロックの名前を入れる
・指定した座標に、``||variables.ブロックのしゅるい||``に入ったブロックを置く
というながれでできそうです！



## 変数と関数をつくる
変数``||variables.ランダムな数||``と``||variables.ブロックのしゅるい||``を作ろう！
また、引数(ひきすう)**x**と**z**をもった関数``||functions.ランダムなブロックをおく||``を作ろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_make_function.gif">



## 条件分岐をつくる
関数``||functions.ランダムなブロックをおく||``の中に、ランダムな数をえらんで条件分岐するしくみを、下をヒントにしながら**自分で考えてプログラミング**しよう！
・``||variables.ランダムな数||``に**1～5のランダムな数**をいれる
・``||variables.ランダムな数||``が**1**のとき: ``||variables.ブロックのしゅるい||``に**TNT**をいれる
・``||variables.ランダムな数||``が**2**のとき: ``||variables.ブロックのしゅるい||``に**レッドストーン鉱石**をいれる
・``||variables.ランダムな数||``が**3**のとき: ``||variables.ブロックのしゅるい||``に**エメラルド鉱石**をいれる
・``||variables.ランダムな数||``が**4**のとき: ``||variables.ブロックのしゅるい||``に**金鉱石**をいれる
・``||variables.ランダムな数||``が**5**のとき: ``||variables.ブロックのしゅるい||``に**ダイヤモンド鉱石**をいれる
・条件分岐の最後が「でなければ」になっているときは、⊕をおしたあとに⊖をおすと、「でなければもし」に変わります！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson9/L9_elseif.gif">

![conditional](https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_conditional.gif)



## えらんだブロックをおく
条件分岐でえらんだブロックを、関数の引数の座標におこう！
・``||blocks.～を(~0, ~0, ~0)に置く||``をはめこみ、座標に``||positions.ワールド(0, 0, 0)||``をはめこむ
・ブロックを``||variables.ブロックのしゅるい||``にする
・座標のx座標とz座標に、引数**x**と**z**をはめこみ、y座標は**70**にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_set_block.gif">
これで、引数xとzでえらんだ場所に、ランダムなブロックをおく関数が完成しました！



## はんいにランダムなブロックをならべるしくみ
作成した関数をつかって、はんいにランダムなブロックをならべるしくみを考えよう！
``||loops.ループ||``をうまくつかえばよさそうです
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_loop_animation.gif">
図を見て、x座標、z座標の数字がどのように変わっているかかくにんしましょう！




## x座標のループ
まずは、x座標について、ブロックをおく場所がどのようにかわっているのか考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_x_axis.png">
x座標は301から310をくりかえしているようです
``||variables.xのはじまり||``に**301**を入れて、``||variables.xのはじまり||``に**0～9の数字をじゅんばんにたしていくループ**を作ればよさそうです！
``||loops.カウンターを0～9に変えてくり返す||``をつかって、くりかえし関数を呼び出そう！



## 変数をつくる
じゅんびとして、``||variables.xのはじまり||``と``||variables.x座標にたす数||``を作ろう！
``||variables.xのはじまり||``には、ブロックをおきはじめるx座標の**301**を入れておこう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_set_variable.png">



## ループをつくる
先ほど考えたことをもとにして、**ランダムなブロックを1れつならべる**ように、**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドrunを入力した時||``のなかに、``||variables.xのはじまり||``に**301**を入れて、``||variables.xのはじまり||``に**0～9の数字をじゅんばんにたしていくループ**を作る
・``||loops.カウンターを0～9に変えてくり返す||``をつかって、くりかえし関数を呼び出す
・``||variables.カウンター||``の部分を``||variables.x座標にたす数||``に変えておく
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_x_axis.png">

```blocks

player.onChat("run", function () {
    for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
        ランダムなブロックをおく(xのはじまり + x座標にたす数, 0)
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
let ブロックのしゅるい = 0
let ランダムな数 = 0
let xのはじまり = 0
xのはじまり = 301

```



## z座標のループをつくる
同じ考え方で、z座標のループも作ることができそうです
z座標が71から80をくりかえすように、下のヒントやx座標のループをもとに**自分で考えてプログラミング**しよう！
・変数``||variables.zのはじまり||``と``||variables.z座標にたす数||``をつくり、``||variables.zのはじまり||``に**71**を入れる
・``||player.チャットコマンドrunを入力した時||``のなかに、``||variables.zのはじまり||``に**0～9の数字をじゅんばんにたしていくループ**を作る
・``||loops.カウンターを0～9に変えてくり返す||``をつかって、くりかえし関数を呼び出す
・``||variables.カウンター||``の部分を``||variables.z座標にたす数||``に変えておく

```blocks

player.onChat("run", function () {
    for (let z座標にたす数 = 0; z座標にたす数 <= 9; z座標にたす数++) {
        for (let x座標にたす数 = 0; x座標にたす数 <= 9; x座標にたす数++) {
            ランダムなブロックをおく(xのはじまり + x座標にたす数, zのはじまり + z座標にたす数)
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
let ブロックのしゅるい = 0
let ランダムな数 = 0
let xのはじまり = 0
let zのはじまり = 0
xのはじまり = 301
zのはじまり = 71

```



## ゲームがおわるときのしくみをつくる
ここまでで、ゲームがはじまって、ランダムにブロックがならぶしくみができました！
次は、``||functions.しゅうりょう||``という関数をつくって、ゲームがおわるときのながれを作りましょう！
・はんいに**岩盤(がんばん)をならべる**
・「しゅうりょう！」とタイトルを表示する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_change_to_bedrock.gif">



## 変数をつくる
先ほど、``||variables.xのはじまり||``と``||variables.zのはじまり||``に、ブロックをならべはじめる座標をいれました
次は、``||variables.xのおわり||``と``||variables.zのおわり||``をつくって、ブロックをならべおわる座標をいれましょう！
y座標は**70**にして、x座標とz座標の数字は、下の図をもとに**自分で考えてみよう**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_stage.png">



## 関数をつくる
先ほど考えたことをもとにして、しゅうりょうするときのしくみを、**自分で考えてプログラミング**しよう！
・``||functions.しゅうりょう||``をつくって、その中に岩盤をならべるプログラムと、「しゅうりょう！」とタイトルを表示するプログラムをつくる
・ブロックをならべる**範囲の始まり**、**範囲のおわり**には、作った変数をつかう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_change_to_bedrock.gif">

```blocks

function しゅうりょう () {
    blocks.fill(
    BEDROCK,
    world(xのはじまり, 70, zのはじまり),
    world(xのおわり, 70, zのおわり),
    FillOperation.Replace
    )
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
let xのはじまり = 0
let zのはじまり = 0
let xのおわり = 0
let zのおわり = 0
xのはじまり = 301
zのはじまり = 71
xのおわり = 310
zのおわり = 80

```



## タイマーのしくみをかんがえる
今度は、せいげんじかんをはかるための**タイマー**のしくみを考えよう！
・``||player.チャットコマンドtimerを入力した時||``の中にプログラムする
・変数``||variables.タイマー||``と``||variables.スイッチ||``をつくる
・``||variables.スイッチ||``が**真**のあいだ、**1秒(1000ミリ秒)まつ⇒``||variables.タイマー||``を1ふやす**をくりかえす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_timer_flow.png">



## 変数をつくる
``||variables.タイマー||``と``||variables.スイッチ||``をつくろう！
``||variables.スイッチ||``は、``||loops.最初だけ||``を実行したときに、**偽**となるようにしておこう



## タイマーをつくる
先ほどのかんがえをもとに、タイマーのしくみを**自分で考えてプログラミング**しよう！
・``||player.チャットコマンドtimerを入力した時||``の中にプログラムする
・``||variables.スイッチ||``が**真**のあいだ、**1秒(1000ミリ秒)まつ⇒``||variables.タイマー||``を1ふやす**をくりかえす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_timer_flow.png">



## タイマーのおわりをつくる
5秒たったときに、先ほどつくった``||functions.しゅうりょう||``を呼び出すように、**自分で考えてプログラミング**しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_change_to_bedrock.gif">


```blocks

player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイマー += 1
        if (タイマー == 5) {
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
    gameplay.title(mobs.target(LOCAL_PLAYER), "しゅうりょう！", "")
}
let タイマー = 0
let スイッチ = false
スイッチ = false

```



## チャットコマンドを呼び出す
最後に、``||player.チャットコマンドrunを入力した時||``の中を完成させよう！
・ゲームのじゅんびとして、最初に``||variables.タイマー||``を0にする
・ステージにブロックをならべる前に、「こうせきをじゅんびちゅう・・・」とメッセージ送信する
・ステージにブロックをならべたあとに、「じゅんびかんりょう！」とメッセージ送信する
・``||variables.スイッチ||``を**真**にして、チャットコマンド**timer**を実行する
・「スタート！　たくさんほろう」とタイトルを表示する



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで**run**と入力しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme3/Lesson11/L11_complete1.gif">
<br></br>
ゲームの開始から終わりまでかくにんしたら、**村人に話しかけよう**

```blocks

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
