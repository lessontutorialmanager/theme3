# プログラムを自由に改造しよう！


```template
player.onChat("run", function (num1) {
    blocks.place(WHITE_TULIP, world(-81, 81, num1))
    blocks.place(ORANGE_TULIP, world(-83, 81, num1))
    blocks.place(RED_TULIP, world(-85, 81, num1))
})
```

# 学んだプログラムを使ってみよう

## プログラムを自由にくみかえよう
チャットで「do ○ ○」と入力したら、指定した位置に好きなブロックが置かれるようにしよう！<br>
<img src="https://i.ibb.co/fQVh1wZ/steps.gif" width="100%">
・``||player.チャットコマンドdoを入力した時||``を作り、右はしにある、⊕を2回押して、``||variables.num1||``、``||variables.num2||``という変数を作る<br>
・``||blocks.ブロックを(~0, ~0, ~0)に置く||``を取り出して、``||player.チャットコマンドdoを入力した時||``にはめ込む<br>
・``||variables.num1||``を範囲の終わりのX座標に、``||variables.num2||``を範囲の終わりのY座標にはめ込み、ブロックの種類を好きなものに変える<br>
こうすると、たとえばチャットで「do 3」と入力すると、設定したブロックが、指定した位置に置かれます！<br>
これを使ってうまく足場を作って移動してみよう！<br>

```blocks
player.onChat("do", function (num1, num2) {
    blocks.place(GOLD_BLOCK, pos(num1, num2, 0))
})


```


## 自由にコードを使ってみよう
`||完了||`をおすと、すべてのコードが使えるようになります<br>
ほかのコードを組み合わせて、もっとすごいプログラムを作れないか、試してみよう！<br>
