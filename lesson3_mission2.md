# LESSON 2 
```block
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        }
    }
    agent.move(UP, 1)
    agent.place(FORWARD)
}
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        check()
        agent.move(RIGHT, 1)
    }
})
```

```template
player.onChat("run", function () {
	
})
```

## 条件分岐を入れ子にしてプログラミングしてみよう @unplugged
エージェントを操作し、法則に従って黄色と黒のテラコッタを設置しよう！<br>
<img style="display: block; margin: auto;" height="100%" width="100%" src="https://i.ibb.co/mF6NyLN/3rd-3-2.png">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・チャットで「run」と入力したら、エージェントがブロックを置くようにプログラミングをする<br>
・くぼみの上と下のブロックが違うブロックなら、黒のテラコッタを置く<br>
・くぼみの上と下のブロックが同じブロックなら、黄色のテラコッタを置く<br>
<img style="width:100%" src="https://i.ibb.co/s3nWvk5/3rd-l3-q2-1.gif"><br>

## 条件分岐と関数を組み合わせよう
まず、1つの縦列について黄色と黒のどちらを置くかを決めることを考えます<br>
手順は次のようになります<br>
①エージェントを上に移動させる</br>
②前にあるブロックが赤いテラコッタか確認させる</br>
③エージェントを下に移動させる</br>
④前にあるブロックが赤いテラコッタか確認させる</br>
⑤エージェントを上に移動させる</br>
⑥上と下のブロックが同じときは黄色のテラコッタを置き、違うときは黒のテラコッタを置く</br>
それを関数としてまとめて、8回繰り返すことを目指しましょう。<br>
<img style="width:100%" src="https://i.ibb.co/CH4JCst/3rd-l3-q2-2.png"><br>

## Step 1

高度なブロックをクリックして、`||functions.関数||`から`||functions.関数を作成する||`を選び、"check"という名前の関数を作りましょう。<br>
<img style="width:100%" src="https://i.ibb.co/9yPXSyQ/3rd-l3-q2-4.gif"><br>
```blocks
function check () {
	
}
player.onChat("run", function () {
	
})
```

## Step 2
エージェントは始めは中央のくぼみの前にいます。まずはくぼみの上側のブロックの色を確認させるために上に移動させましょう<br>
`||agent.エージェント||`から`||agent.エージェントを 前 に 1 ブロック移動させる||`を取り出して関数の中に入れ、方向を上に変えます。<br>
```blocks
function check () {
    agent.move(UP, 1)
}
player.onChat("run", function () {
	
})
```

## Step 3
ブロックの色が赤か青かによって処理が分かれるので、`||logic.条件分岐||`を使います</br>
`||logic.論理||`から`||logic.もし 真 なら ～ でなければ ～||`を取り出し、`||agent.エージェントを 上 に 1 ブロック移動させる||`の下に入れます。<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (true) {
    	
    } else {
    	
    }
}
player.onChat("run", function () {
	
})
```

## Step 4
ブロックが赤色のブロックであるかどうかを確かめるために、`||logic.論理||`から`||logic.0 = 0||`を取り出して、`||logic.真||`の部分にあてはめます。<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (0 == 0) {
    	
    } else {
    	
    }
}
player.onChat("run", function () {
	
})

```

## Step 5
左側の0を`||agent.エージェントの 前 のブロック||`に変更します。<br>
また、`||blocks.ブロック||`から`||blocks.[草ブロック]||`を取り出し、右側の0にあてはめます。<br>
その後、ブロックの種類を[赤色の彩釉テラコッタ]に変更します。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
    	
    } else {
    	
    }
}
player.onChat("run", function () {
	
})

```

## Step 6
上側のブロックが赤色の場合を考えます。<br>
くぼみの下側のブロックの色を確認するためにエージェントを下に移動させましょう。<br>
`||agent.エージェントを 下 に 2 ブロック移動させる||`を`||logic.もし ～ なら||`の中に入れます。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
    } else {
    	
    }
}
player.onChat("run", function () {
	
})

```

## Step 7
下側のブロックの色を確認するために、エージェントを下に移動させましょう<br>
`||logic.もし 真 なら ～ でなければ ～||`、`||logic.0 = 0||`、`||agent.エージェントの 前 のブロック||`、`||blocks.赤色の彩釉テラコッタ||`を取り出し、
同じように条件分岐を作って`||agent.エージェントを 下 に 2 ブロック移動させる||`の下に入れます。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        	
        } else {
        	
        }
    } else {
    	
    }
}
player.onChat("run", function () {
	
})
```

## Step 8
下側のブロックも赤色の場合、上と下のブロックは同じ色ですから、くぼみには**黄色のテラコッタ**を置けばよいということになります。<br>
`||agent.エージェントに [草ブロック] を 1 個、自分のスロット 1 番に設定させる||`を取り出し、[草ブロック]を[黄色のテラコッタ]に変更します。<br>
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
        	
        }
    } else {
    	
    }
}
player.onChat("run", function () {
	
})

```

## Step 9
内側の条件分岐のうち、「でなければ」の中について考えます。<br>
ここに入るのは、上側が赤色で下側が青色の時ですから、くぼみには**黒色のテラコッタ**を置けばよいということになります。<br>
`||agent.エージェントに [草ブロック] を 1 個、自分のスロット 1 番に設定させる||`を取り出し、[草ブロック]を[黒色のテラコッタ]に変更します。<br>
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
    	
    }
}
player.onChat("run", function () {
	
})

```

## Step 10
外側の条件分岐の「でなければ」の部分について考えます。<br>
条件分岐の外側の時点では、エージェントは上側のブロックの前にいるので、まずは下側のブロックの前まで移動します。<br>
`||agent.エージェントを 下 に 2 ブロック移動させる||`を`||logic.でなければ ～ ||`の中に入れます。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
        agent.move(DOWN, 2)
    }
}
player.onChat("run", function () {
	
})

```

## Step 11
外側の条件分岐の「でなければ」の部分は、上側のブロックが青色である場合に当たります。<br>
下側のブロックを見るところから先は、結果が逆になること以外はほぼ同じことをすればよいです。
<br>
内側の条件分岐の`||logic.もし … なら ～ でなければ ～||`の部分を**右クリック**し、**複製する**を選んで
外側の条件分岐の`||logic.でなければ ～||`の中の`||agent.エージェントを 下 に 2 ブロック移動させる||`の下に置きます。
<br>
２つ目の条件分岐の黄色のテラコッタを黒色のテラコッタに、黒色のテラコッタを黄色のテラコッタに変えましょう<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        }
    }
}
player.onChat("run", function () {
	
})

```

## Step 12

すべてのパターンについてエージェントに持たせるブロックを設定したところで、ブロックを設置していきます。
<br>
今エージェントは下側のブロックの前にいますから、くぼみの前に移動します。<br>
外側の条件分岐の下に、`||agent.エージェントを 上 に 1 ブロック移動させる||`と`||agent.エージェントに 前 へ置かせる||`を置きます。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        }
    }
    agent.move(UP, 1)
    agent.place(FORWARD)
}
player.onChat("run", function () {
	
})

```

## Step 13

これで1列分についてプログラムを作ることができました。<br>
あとはこれを右へ移動しながら8回繰り返せばよいです。
<br>

`||player.チャットコマンド "run" を入力した時||`の中に、`||loop.くりかえし 8 回||`を入れ、
その中に`||functions.呼び出し check||`と`||agent.エージェントを 右 に 1 ブロック移動させる||`を入れます。
<br>
```blocks
function check () {
    agent.move(UP, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        }
    } else {
        agent.move(DOWN, 2)
        if (agent.inspect(AgentInspection.Block, FORWARD) == RED_GLAZED_TERRACOTTA) {
            agent.setItem(BLACK_TERRACOTTA, 1, 1)
        } else {
            agent.setItem(YELLOW_TERRACOTTA, 1, 1)
        }
    }
    agent.move(UP, 1)
    agent.place(FORWARD)
}
player.onChat("run", function () {
    for (let index = 0; index < 8; index++) {
        check()
        agent.move(RIGHT, 1)
    }
})

```

## Step 14
これで完成です。右下の実行ボタンを押し、チャットコマンドに "run" と打ってみましょう。
