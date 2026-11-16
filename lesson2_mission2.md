# LESSON2 砂のエレベーターをつくろう
```block
function doSomething () {
    for (let index = 0; index < 9; index++) {
        blocks.place(SAND, pos(0, 0, 0))
        player.teleport(pos(0, 1, 0))
        loop.pause(500)
    }
}
player.onItemInteracted(STICK, function () {
    doSomething()
    loops.pause(5000)
    doSomething2()
})
```

```template
player.onChat("run", function () {
	
})
```

## 1.ブロックをその場に置けるようにしよう

`||blocks.ブロック||`ボタンをクリックしてその中の`||blocks.ブロックを～に置く||`と書いてあるブロックを中央までドラックしてみましょう</br>
`||blocks.土ブロック||`をクリックして`||blocks.砂||`に変えましょう
<img style= "width:100%" src="https://i.ibb.co/tKhPrP3/M2-0gif.gif"><br>


## 2.１ブロック上にテレポートできるようにしよう

`||player.プレイヤー||`ボタンをクリックしてその中の`||player.～にテレポートする||`を取り出し、さっきの`||blocks.ブロックを～に置く||`の下にひっつけよう</br>
座標を<~0 ~1 ~0>にしよう</br>
<img style= "width:100%" src="https://i.ibb.co/2jvZ6wq/M2-1gif.gif"><br>

## 3.ループの中に３つまとめていれよう

`||loops.ループ||`ボタンをクリックしてその中の`||loops.くりかえし||`と`||loops.一時停止||`を取り出そう</br>
`||loops.一時停止||`を`||player.～にテレポートする||`の下にひっつけよて、３つまとめて`||loops.くりかえし||`の中にいれよう</br>
<img style= "width:100%" src="https://i.ibb.co/SnnChyf/M2-3gif.gif"><br>

## 3.関数を棒で呼び出そう
Lesson1と同じようにループごと関数の中にいれて、棒を使ったときに呼び出しできるようにしよう
<img style= "width:100%" src="https://i.ibb.co/C8xVdfz/M2-4gif.gif"><br>

## 4.『実行』ボタンをクリックしましょう
画面右下にある緑の『▶』ボタンをクリックして作ったプログラムを実行し、棒を使ってみよう
