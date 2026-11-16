# LESSON 2 
```block
player.onChat("run", function (種類, 長さ) {
    ブロックを選ぶ(種類, 長さ)
})
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    }
}



```

```template
player.onChat("run", function () {
	
})
```

## 変数と関数と条件分岐を使ってプログラミングしてみよう @unplugged
条件分岐で設置するブロックを決めよう！<br>
<img style="display: block; margin: auto;" height="40%" width="40%" src="https://i.ibb.co/LS4wtbR/l1-2-1.png">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・プレイヤーは必ず橋の左前に乗ってプログラムを実行する<br>
・チャットで「run ○ □」（○はブロックの種類、□は橋の長さ）と入力したら、指定したブロックで指定した長さだけ橋を作る<br>
・0は白色の色付きガラス、1は黄緑色の色付きガラス、2は空色の色付きガラスにする<br>
<img style="width:100%" src="https://i.ibb.co/JydFJNZ/l1-2-2.gif"><br>

## 関数を作ろう
まずはブロックの種類と橋の長さを変えられるように関数を作りましょう<br>
<img style="width:100%" src="https://i.ibb.co/x8G1sgk/l1-2-3.png"><br>

## Step 1
高度なブロックをクリックして、`||functions.関数||`をクリックします</br>
`||functions.関数を作成する…||`をクリックして、【doSomething】を【ブロックを選ぶ】に入力しなおします</br>
『パラメーターを追加する』の『数値』をクリックして、【数値】を【種類】に入力しなおします</br>
もう一度『パラメーターを追加する』の『数値』をクリックして、【数値】を【長さ】に入力しなおしてから完了をクリックします<br>

```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
	
}
player.onChat("run", function () {
	
})


```

## Step 2
次は関数「ブロックを選ぶ」の中に条件分岐を作ります</br>
`||logic.論理||`から`||logic.もし真なら　でなければ||`を関数の中に入れます</br>
条件分岐の下にある⊕を２回クリックしたら、３つ目の「でなければ⊝」の⊝をクリックします<br>
<img style="width:100%" src="https://i.ibb.co/mzf2s8L/l1-2-4.gif"><br>
<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (true) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    }
}
player.onChat("run", function () {
	
})


```

## Step 3
入力した数字によって設置するブロックを変えましょう</br>
`||logic.論理||`から`||logic.0=0||`を３つ取り出し、すべての『もし◇なら』に重ねます<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (0 == 0) {
    	
    } else if (0 == 0) {
    	
    } else if (0 == 0) {
    	
    }
}
player.onChat("run", function () {
	
})


```

## Step 4
`||functions.関数 ブロックの種類||`の`||agent.種類||`をドラッグしてすべての`||logic.0=0||`の左の0に重ねます</br>
次に`||logic.種類=0||`の0を上から順に0、1、2と入力しなおしましょう<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
    	
    } else if (種類 == 1) {
    	
    } else if (種類 == 2) {
    	
    }
}
player.onChat("run", function () {
	
})



```

## Step 5
ブロックを設置するプログラムを作りましょう<br>
`||blocks.ブロック||`から`||blocks.ブロックを並べる～||`を３つ取り出し、条件分岐の中にそれぞれ入れましょう<br>

```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        GRASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        GRASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        GRASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    }
}
player.onChat("run", function () {
	
})


```

## Step6
ブロックを上から白色の色付きガラス、黄緑色の色付きガラス、空色の色付きガラスに変えます<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        pos(0, 0, 0),
        pos(0, 0, 0),
        FillOperation.Replace
        )
    }
}
player.onChat("run", function () {
	
})

## Step7
ブロックを設置する座標と長さをプログラミングしましょう</br>
`||positions.ポジション||`から`||positions.右0 上0 前0||`を６つ取り出し、`||blocks.ブロックを並べる～||`の範囲の始まりと範囲の終わりにそれぞれ重ねましょう<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        posCamera(0, 0, 0),
        posCamera(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        posCamera(0, 0, 0),
        posCamera(0, 0, 0),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        posCamera(0, 0, 0),
        posCamera(0, 0, 0),
        FillOperation.Replace
        )
    }
}
player.onChat("run", function () {
	
})



```

## Step8
すべての`||positions.範囲の始まり 右0 上0 前0||`を`||positions.右0 上-1 前1||`にしましょう</br>
次にすべての`||positions.範囲の終わり 右0 上0 前0||`を`||positions.右1 上-1 前0||`にしましょう</br>
最後にすべての`||positions.範囲の終わり 右1 上-1 前0||`の前０に関数の『長さ』をドラッグして、`||positions.右1 上-1 前(長さ)||`にしましょう<br>
```blocks
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    }
}
player.onChat("run", function () {
	
})

```

## Step9
「run ○ □」（○はブロックの種類、□は橋の長さの数字）と入力した時に関数が実行されるようにしましょう</br>
`||player.チャットコマンドrunを入力した時⊕||`の`||player.⊕||`をクリックします</br>
num1をクリックして変数を作成する…を選んで、【種類】と入力します</br>
もう一度`||player.チャットコマンドrunを入力した時⊕||`の`||player.⊕||`をクリックします</br>
num1をクリックして変数を作成する…を選んで、【長さ】と入力します<br>
```blocks
player.onChat("run", function (種類, 長さ) {
	
})
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    }
}



```

## Step10
`||functions.関数||`から`||functions.呼び出し ブロックの種類 １ １||`をrunの中に入れます</br>
`||variables.変数||`から`||variables.種類||`を`||functions.呼び出し ブロックの種類 １ １||`の`||functions.左の１||`に重ねます</br>
`||variables.変数||`から`||variables.長さ||`を`||functions.呼び出し ブロックの種類 種類 １||`の`||functions.右の１||`に重ねます<br>
```blocks
player.onChat("run", function (種類, 長さ) {
    ブロックを選ぶ(種類, 長さ)
})
function ブロックを選ぶ (種類: number, 長さ: number) {
    if (種類 == 0) {
        blocks.fill(
        WHITE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 1) {
        blocks.fill(
        LIME_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    } else if (種類 == 2) {
        blocks.fill(
        LIGHT_BLUE_STAINED_GLASS,
        posCamera(0, -1, 1),
        posCamera(1, -1, 長さ),
        FillOperation.Replace
        )
    }
}



```

## Step 11
これで完成です</br>
右下の実行ボタンを押し、矢印ブロックの上に立ってチャットコマンドに "run ○ □"（○はブロックの種類、□は橋の長さの数字） と打ってみましょう<br>
<img style="width:100%" src="https://i.ibb.co/JydFJNZ/l1-2-2.gif"><br>
