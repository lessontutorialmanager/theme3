# 色々な顔をつくろう！


```blocks

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

```template

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

## 色々な顔をつくろう！ @unplugged
好きな顔を作ろう！<br>



## 例1
関数の条件分岐を増やして、いろいろなキャラクターの顔をプログラミングで作ってみよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_cow.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_zombie.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_enderman.png">



## 例2
``||player.チャットコマンドrunを入力した時||``の⊕を押して``||variables.num1||``を追加し、``||variables.num1||``に入った数字のキャラクターの顔が作られるようにしよう<br>

```blocks

let スタート座標: Position = null
player.onChat("run", function (num1) {
    スタート座標 = world(51, 81, 122)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標, num1)
        頭(スタート座標, num1)
        目(スタート座標, num1)
        はなと口(スタート座標, num1)
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

## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります<br>
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！<br>