# ブタの顔を作ろう！

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
    スタート座標 = world(59, 74, 142)
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
function 顔 (開始位置: Position) {
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
}
function 頭 (開始位置: Position) {
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
}
function 目 (開始位置: Position) {
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
}
function はなと口 (開始位置: Position) {
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
}
player.onChat("run", function () {
    スタート座標 = world(59, 74, 142)
    for (let index = 0; index < 8; index++) {
        顔(スタート座標)
        頭(スタート座標)
        目(スタート座標)
        はなと口(スタート座標)
        スタート座標 = positions.add(
        スタート座標,
        pos(1, 0, 0)
        )
    }
})

```

## ブタの顔を作ろう！ @unplugged
ブタの顔を作ろう！<br>
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete2.gif">



## 目標
先ほどの関数に**引数**を追加して、ブタの顔のパーツを選択できるようにしよう！<br>
・チャットコマンドで「run」と入力すると、ブタの顔の形にブロックを並べる<br>
・たて、横、高さが**8ブロック**の大きさにする<br>
・用意してある変数``||variables.スタート座標||``を基準にブロックを並べる<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face2.png">



## 手順を考える
まずは関数に**数値**の引数**種類**を追加しよう！<br>
その後、それぞれの関数に条件分岐を追加して、**引数「種類」の数値が**1**なら**スティーブ**、**2**なら**ブタ**の顔のパーツを選べるようにしよう<br>
・使うブロックは、下の画像を確認しよう！<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face2_with_color.png">





## Step1 関数を編集する
引数**数値**を追加しよう！<br>
・関数を**右クリック**して、「関数の編集」を押す<br>
・**数値**の引数**種類**を追加する<br>
※4つの関数``||functions.顔||``、``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``の**全て**に同じことをしよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_edit_functions.gif">

```blocks
function 顔 (開始位置: Position, 種類: number) {
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
}
function 頭 (開始位置: Position, 種類: number) {
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
}
function 目 (開始位置: Position, 種類: number) {
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
}
function はなと口 (開始位置: Position, 種類: number) {
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
}

```



## Step2 条件分岐を追加する①
スティーブとブタ、どちらの顔のパーツのブロックを並べるのか、**条件分岐**をそれぞれの**関数**へ追加しよう！<br>
・もし**数値**が**1**ならスティーブ、**2**ならブタのパーツを選べるようにする<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_conditional.png">



## Step2 条件分岐を追加する➁
条件分岐を追加しよう！<br>
・``||logic.論理||``から``||logic.もし～なら でなければ||``を取り出して、スティーブの顔を作るプログラムが``||logic.もし～なら||``に入るようにはめ込む<br>
・``||logic.もし～なら でなければ||``の⊕を押したあと⊖を押して、条件を2種類入れられるようにする<br>
・1つ目の条件が``||logic.種類 = 1||``、2つ目の条件が``||logic.種類 = 2||``となるように設定する<br>
※4つの関数``||functions.顔||``、``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``の**全て**に同じことをしよう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_set_conditionals.gif">

```blocks

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
    } else if (種類 == 2) {}
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
    } else if (種類 == 2) {}
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
    } else if (種類 == 2) {}
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
    } else if (種類 == 2) {}
}

```



## Step3 ブロックを並べる
4つの関数``||functions.頭||``、``||functions.目||``、``||functions.はなと口||``の``||logic.種類 = 2||``のときに、ブタの顔を作るブロックが並べられるよう、プログラミングを**自分で考えてやってみよう！**<br>
使うブロックは以下を確認しよう<br>
・``||functions.顔||``：桃色のコンクリート<br>
・``||functions.頭||``：なし(なにもブロックを入れない)<br>
・``||functions.目||``：白色のコンクリート、黒色のコンクリート<br>
・``||functions.はなと口||``：白色のテラコッタ、赤紫色のコンクリート<br>
※ブロックを**1つ**だけおきたいときは、``||blocks.ブロック||``の``||blocks.ブロックを(~0, ~0, ~0)に置く||``を使おう<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face2.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_face2_with_color.png">

```blocks

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



## Step4 関数を実行する
``||player.チャットコマンドrunを入力した時||``を入力した時にブタの顔を作る関数を呼び出すようにしよう<br>
・``||functions.呼び出し 顔||``、``||functions.呼び出し 頭||``、``||functions.呼び出し 目||``、``||functions.呼び出し はなと口||``の2つ目の引数をすべて**2**にする<br>
こうすることで、**種類**に2が入り、4つの関数の``||logic.種類 = 2||``のときのプログラムが実行されます！<br>
<br></br>

```blocks

let スタート座標: Position = null
player.onChat("run", function () {
    スタート座標 = world(59, 74, 142)
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



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう<br>
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったらチャットで「run」と入力してブタの顔の形にブロックを並べよう！<br>
うまくいかなかったときは、**座標を自分で修正してみよう**<br>
できあがったら、**村人に話しかけよう**<br>
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/3rd/Lesson6/L6_complete2.gif">




