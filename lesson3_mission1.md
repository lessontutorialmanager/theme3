# LESSON 1 
```block
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        for (let index = 0; index < 4; index++) {
            agent.setItem(RED_SANDSTONE, 1, 1)
            agent.place(FORWARD)
            agent.move(UP, 1)
        }
        agent.move(RIGHT, 1)
        agent.move(DOWN, 4)
    }
})
```

```template
player.onChat("run", function () {
	
})
```

## 入れ子を使ってプログラミングしてみよう @unplugged
エージェントを操作して入口の奥のくぼみを埋めよう！<br>
<img style="display: block; margin: auto;" height="40%" width="40%" src="https://i.ibb.co/RjTgBpt/3rd-3-1.gif">

## 目標
まずはこれから作るものの形を確認しよう！<br>
・チャットで「run」と入力したら、エージェントがブロックを置くようにプログラミングをする<br>
・エージェントが縦に４つブロックを置いた後に次のブロックを置く位置に移動する<br>
・くぼみがすべて埋まるまでくり返す<br>
<img style="width:100%" src="https://i.ibb.co/RjTgBpt/3rd-3-1.gif"><br>

## くぼみの縦を埋めるプログラムを作ろう
まずはくぼみの縦１列だけ埋めるプログラムを作りましょう<br>
<img style="width:100%" src="https://i.ibb.co/b5ZCYWQ/3rd-l3-q1-3.gif"><br>

## Step 1
はじめに、エージェントに縦１列を赤い砂岩で埋めるプログラムを作りましょう<br>
`||loops.ループ||`から`||loops.くりかえし４回||`を取り出し、`||player.チャットコマンド "run" を入力した時||`の中に入れます</br><br>
<img style="width:100%" src="https://i.ibb.co/7nk3fY6/3rd-l3-q1-4.gif"><br>

```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
    	
    }
})

```

## Step 2
`||agent.エージェント||`から`||agent.エージェントに [ブロック] を 1 個、自分のスロット 1 番に設定させる||`を取り出し、`||loops.くりかえし４回||`の中に入れます</br>
`||blocks.草ブロック||`をクリックして、`||blocks.赤い砂岩||`を選びましょう<br>
<img style="width:100%" src="https://i.ibb.co/qW89V7s/3rd-l3-q1-5.gif"><br>
<br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        agent.setItem(RED_SANDSTONE, 1, 1)
    }
})

```

## Step 3
`||agent.エージェント||`から`||agent.エージェントに 前 へ置かせる||`を取り出し、`||agent.エージェントに [ブロック] を 1 個、自分のスロット 1 番に設定させる||`の下に入れます
<br>
<img style="width:100%" src="https://i.ibb.co/B4f80sN/3rd-l3-q1-6.gif"><br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        agent.setItem(RED_SANDSTONE, 1, 1)
        agent.place(FORWARD)
    }
})

```

## Step 4
ブロックを置いた後は、1つ上のブロックへ移動させます</br>
`||agent.エージェント||`から`||agent.エージェントを 前 に 1 ブロック移動させる||`を取り出し、`||agent.エージェントに 前 へ置かせる||`の下に入れましょう</br>
そして、`||前||`を`||上||`に変更します
<br>
<img style="width:100%" src="https://i.ibb.co/9pz6RRj/3rd-l3-q1-7.gif"><br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        agent.setItem(RED_SANDSTONE, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
    }
})

```

## 次のブロックを置く位置に移動させる方法を考えよう
「1列目を置いた後、2列目を置き始めるためにはどうすればよいか」ということを考えましょう<br>
エージェントが現在いる位置から次のブロックを置き始める位置に移動するにはどんなプログラムが必要でしょうか？</br>
<br>
<img style="width:100%" src="https://i.ibb.co/Bg0b4bz/3rd-l3-q1-8.png"><br>

## Step 5
1列目を置き終わった後の場所から、2列目を置き始める場所に移動するには、「右に1ブロック、下に4ブロック」移動すればよさそうです<br>
`||agent.エージェントを 右 に 1 ブロック移動させる||`と`||agent.エージェントを 下 に 4 ブロック移動させる||`をくりかえし４回の下に入れてみましょう
<br>
<img style="width:100%" src="https://i.ibb.co/cvL2x1Y/3rd-l3-q1-9.gif"><br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        agent.setItem(RED_SANDSTONE, 1, 1)
        agent.place(FORWARD)
        agent.move(UP, 1)
    }
    agent.move(RIGHT, 1)
    agent.move(DOWN, 4)
})

```

## くり返しの入れ子を使おう
これまでで作ったプログラムを４列分くり返す必要があります<br>
どのようにすればくり返せるでしょうか？</br>
くり返しを使ったプログラムを、さらにくり返すことを『くり返しの入れ子』と言います</br>
『入れ子』を使ってプログラムをくり返してみましょう</br>
<br>
<img style="width:100%" src="https://i.ibb.co/nQ7x3Hd/3rd-l3-q1-10.png"><br>

## Step 6
`||loops.くりかえし４回||`で今まで作ったプログラムをはさみましょう
<br>
<img style="width:100%" src="https://i.ibb.co/mXvcMKk/3rd-l3-q1-11.gif"><br>
```blocks
player.onChat("run", function () {
    for (let index = 0; index < 4; index++) {
        for (let index = 0; index < 4; index++) {
            agent.setItem(RED_SANDSTONE, 1, 1)
            agent.place(FORWARD)
            agent.move(UP, 1)
        }
        agent.move(RIGHT, 1)
        agent.move(DOWN, 4)
    }
})
```

## Step 7
これで完成です右下の実行ボタンを押し、チャットコマンドに "run" と打ってみましょう
