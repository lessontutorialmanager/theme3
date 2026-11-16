# 顔のパーツをランダムに選ぼう！

```blocks
let スタート座標: Position = null
let 顔の種類 = 0
let 頭の種類 = 0
let 目の種類 = 0
let はなと口の種類 = 0
function 顔 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        LIGHT_GRAY_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        PINK_CONCRETE,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    }
}
function 頭 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 1)
        ))
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 8)
        ))
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 7, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
    	
    }
}
function 目 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 2)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 3)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 7)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 6)
        ))
    } else if (種類 == 2) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 2)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 1)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 7)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 8)
        ))
    }
}
function はなと口 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        BROWN_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 3, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 3, 5)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 6)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 5)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 4, 6)
        ),
        FillOperation.Replace
        )
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 3)
        ))
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 6)
        ))
    }
}
player.onChat("run", function () {
    スタート座標 = world(51, 81, 122)
    顔の種類 = randint(1, 2)
    頭の種類 = randint(1, 2)
    目の種類 = randint(1, 2)
    はなと口の種類 = randint(1, 2)
    for (let index = 0; index < 16; index++) {
        顔(スタート座標, 顔の種類)
        頭(スタート座標, 頭の種類)
        目(スタート座標, 目の種類)
        はなと口(スタート座標, はなと口の種類)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})

```

```template
let スタート座標: Position = null
function 顔 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        LIGHT_GRAY_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        PINK_CONCRETE,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    }
}
function 頭 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 1)
        ))
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 8)
        ))
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 7, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
    	
    }
}
function 目 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 2)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 3)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 7)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 6)
        ))
    } else if (種類 == 2) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 2)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 1)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 7)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 8)
        ))
    }
}
function はなと口 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        BROWN_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 3, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 3, 5)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 6)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 5)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 4, 6)
        ),
        FillOperation.Replace
        )
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 3)
        ))
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 6)
        ))
    }
}
player.onChat("run", function () {
    スタート座標 = world(51, 81, 122)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標, 2)
        頭(スタート座標, 2)
        目(スタート座標, 2)
        はなと口(スタート座標, 2)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})

```

## 顔のパーツをランダムに選ぼう！ @unplugged
顔のパーツをランダムに選べるようにしよう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete3.gif">



## 目標
顔のパーツをランダムに変えられるようにしよう！<br>
・チャットで「run」と入力するたびに、それぞれのパーツについて、スティーブの顔とブタの顔のどちらかがランダムに並べられる<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete3.gif">



## 手順を考える
変数を用意して、その中に1か2の数字のどちらかをランダムに入れるようにしよう<br>
・変数``||variables.顔の種類||``、``||variables.頭の種類||``、``||variables.目の種類||``、``||variables.はなと口の種類||``を用意する<br>
・``||math.ランダムな数字を選択||``を使って、1か2をランダムに選んでそれぞれの変数に入れる<br>
・関数の引数**種類**に、ランダムな数字が入った変数をはめ込む<br>




## Step1 変数を用意する
4つの変数``||variables.顔の種類||``、``||variables.頭の種類||``、``||variables.目の種類||``、``||variables.はなと口の種類||``を作ろう！<br>



## Step2 変数にランダムな数字を入れる
用意した変数に1か2の数字のどちらかをランダムに入れるようにしよう<br>
・``||variables.変数||``から``||variables.変数 顔の種類を0にする||``、``||variables.変数 頭の種類を0にする||``、``||variables.変数 目の種類を0にする||``、``||variables.変数 はなと口の種類を0にする||``を取り出して、``||variables.変数 スタート座標をワールド(51, 81, 122)にする||``の**下**にはめ込む<br>
・``||math.計算||``から``||math.ランダムな数字を選択||``を取り出してすべてにはめ込む<br>
・``||math.ランダムな数字を選択||``の数字の範囲を**1から2**にする<br>
これで、4つの変数に1か2のどちらかが入りました！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_randint.png">



## Step3 引数に変数を入れる
最後に、4つの変数を関数の引数**種類**に入れよう<br>
・変数``||variables.顔の種類||``、``||variables.頭の種類||``、``||variables.目の種類||``、``||variables.はなと口の種類||``を関数の呼び出しの2つ目の引数にはめ込む<br>

```blocks

let スタート座標: Position = null
let 顔の種類 = 0
let 頭の種類 = 0
let 目の種類 = 0
let はなと口の種類 = 0
player.onChat("run", function () {
    スタート座標 = world(51, 81, 122)
    顔の種類 = randint(1, 2)
    頭の種類 = randint(1, 2)
    目の種類 = randint(1, 2)
    はなと口の種類 = randint(1, 2)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標, 顔の種類)
        頭(スタート座標, 頭の種類)
        目(スタート座標, 目の種類)
        はなと口(スタート座標, はなと口の種類)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})
function 顔 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        LIGHT_GRAY_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        PINK_CONCRETE,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    }
}
function 頭 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 1)
        ))
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 8)
        ))
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 7, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
    	
    }
}
function 目 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 2)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 3)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 7)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 6)
        ))
    } else if (種類 == 2) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 2)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 1)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 7)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 8)
        ))
    }
}
function はなと口 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        BROWN_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 3, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 3, 5)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 6)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 5)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 4, 6)
        ),
        FillOperation.Replace
        )
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 3)
        ))
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 6)
        ))
    }
}


```

## Step4 顔の厚みを変える
顔をもっと飛び出させたいので、顔の厚みが**16ブロック**になるように**自分で考えてプログラミングしよう！**<br>

```blocks
let スタート座標: Position = null
let 顔の種類 = 0
let 頭の種類 = 0
let 目の種類 = 0
let はなと口の種類 = 0
function 顔 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        LIGHT_GRAY_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        PINK_CONCRETE,
        positions.add(
        開始位置,
        pos(0, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    }
}
function 頭 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 1)
        ))
        blocks.place(BLACK_TERRACOTTA, positions.add(
        開始位置,
        pos(0, 6, 8)
        ))
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 7, 1)
        ),
        positions.add(
        開始位置,
        pos(0, 8, 8)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
    	
    }
}
function 目 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 2)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 3)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 7)
        ))
        blocks.place(BLUE_CONCRETE, positions.add(
        開始位置,
        pos(0, 4, 6)
        ))
    } else if (種類 == 2) {
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 2)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 1)
        ))
        blocks.place(WHITE_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 7)
        ))
        blocks.place(BLACK_CONCRETE, positions.add(
        開始位置,
        pos(0, 5, 8)
        ))
    }
}
function はなと口 (開始位置: Position, 種類: number) {
    if (種類 == 1) {
        blocks.fill(
        BROWN_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 3, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 3, 5)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        BLACK_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 1, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 6)
        ),
        FillOperation.Replace
        )
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 4)
        ),
        positions.add(
        開始位置,
        pos(0, 2, 5)
        ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        WHITE_TERRACOTTA,
        positions.add(
        開始位置,
        pos(0, 2, 3)
        ),
        positions.add(
        開始位置,
        pos(0, 4, 6)
        ),
        FillOperation.Replace
        )
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 3)
        ))
        blocks.place(MAGENTA_CONCRETE, positions.add(
        開始位置,
        pos(0, 3, 6)
        ))
    }
}
player.onChat("run", function () {
    スタート座標 = world(51, 81, 122)
    顔の種類 = randint(1, 2)
    頭の種類 = randint(1, 2)
    目の種類 = randint(1, 2)
    はなと口の種類 = randint(1, 2)
    for (let index = 0; index < 16; index++) {
        顔(スタート座標, 顔の種類)
        頭(スタート座標, 頭の種類)
        目(スタート座標, 目の種類)
        はなと口(スタート座標, はなと口の種類)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})

```


## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったらチャットで「run」と入力してみよう！<br>
気に入った顔になるまで、何度かくりかえしてみよう<br>
できあがったら、**村人に話しかけよう**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete3.gif">
