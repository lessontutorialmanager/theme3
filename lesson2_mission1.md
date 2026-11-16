# LESSON1 砂の階段を作ってみよう
```block
function one () {
    blocks.fill(
    SANDSTONE,
    world(9, 63, -53),
    world(9, 63, -48),
    FillOperation.Replace
    )
}
player.onItemInteracted(STICK, function () {
    wa()
})
```

## 砂の階段を作ってみよう @unplugged
落ちる砂を生かして階段を作ろう<br>
<img style="display: block; margin: auto;" height="100%" width="100%" src="https://i.ibb.co/74shbrQ/M1-4.gif">

## 目標（もくひょう）
まずはこれから作るものの形をかくにんしよう！<br>
・棒を1回振ったら砂の塊が落ちて階段が出来るようにプログラミングをする<br>
・砂を上から落としていく仕組みを作ろう<br>
・高次な関数で5回呼び出して上に登れるようにしよう<br>
<img style= "width:100%" src="https://i.ibb.co/4FTyxCn/M1-0gif.gif"><br>

## 1.砂を空中に横一列に並べるしくみをつくろう
`||blocks.ブロック||`ボタンをクリックしてその中の`||blocks.ブロックを並べる||`と書いてあるブロックを中央までドラックしてみましょう</br>
`||blocks.土ブロック||`をクリックして`||blocks.砂||`に変えましょう</br>
`||positions.ポジション||`ボタンをクリックしてその中の`||positions.ワールド0 0 0||`を`||blocks.範囲の始まり~0~0~0||`の上までドラッグします</br>
`||positions.範囲の始まり ワールド0 0 0||`を`||positions.ワールド9 63 -53||`に変えよう</br>
同じやり方で`||blocks.範囲の終わり~0~0~0||`の上に`||positions.ワールド9 63 -48||`をつくろう</br>
<img style= "width:100%"  src="https://i.ibb.co/1fkHWdZ/M1-1.gif"><br>

## 2.砂を空中に並べる関数にしよう
`||advanced.高度なブロック||`から関数を作成して「sand」と名前をつけよう<br>
`||advanced.「sand」関数||`の中にさっき作った`||blocks.砂を並べるしくみ||`を入れよう<br>
<img style="width:100%"  src="https://i.ibb.co/fHz5t7P/M1-2.gif">

## 3.「棒」を使ったら関数を呼び出せるようにしよう

`||player.プレイヤー||`から`||「次のアイテムを使った時」||`をとりだして、棒を設定しよう<br>
`||advanced.高度なブロック||`から`||advanced.「呼び出し sand」||`をとりだして、`||player.「次のアイテムを使った時」||`にいれよう<br>
<img style="width:100%"  src="https://i.ibb.co/8b6YHb0/M1-3.gif"><br>

## 4.『実行』ボタンをクリックしましょう
画面右下にある緑の『▶』ボタンをクリックして作ったプログラムを実行し、棒を振ってみましょう<br>
