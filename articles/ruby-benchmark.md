---
title: "Ruby Benchmark を使ってみる"
emoji: "😽"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Ruby"]
published: true
---

Rubyのモジュールとして提供されているBenchmarkを使用してプログラム実行時のCPU処理にかかった時間を知ることができます。
Benchmarkとは本来[基準, 指標]などの意味があり、よくソフトウェアの性能を定量的に比較するためにベンチマークテストが行われる。


公式ドキュメントを参照して、簡単なものを実行
```ruby
require 'benchmark'

Benchmark.benchmark(Benchmark::CAPTION, 10, Benchmark::FORMAT) do |x|
  x.report("for_in: ") { for i in 1..1000; a = "test"; end }
  x.report("times: ") { 1000.times do ; a = "test"; end }
  x.report("upto: ") { 1.upto(1000) do ; a = "test"; end }
end

# ↓ 出力結果
                 user     system      total        real
for_in:      0.001906   0.000002   0.001908 (  0.001909)
times:       0.001160   0.000004   0.001164 (  0.001167)
upto:        0.000685   0.000001   0.000686 (  0.000687)
=> [#<Benchmark::Tms:0x00007fe2fe9547a8 @label="for_in: ", @real=0.0019089998677372932, @cstime=0.0, @cutime=0.0, @stime=2.000000000002e-06, @utime=0.0019059999999999633, @total=0.0019079999999999653>, #<Benchmark::Tms:0x00007fe2fe9be5e0 @label="times: ", @real=0.0011669998057186604, @cstime=0.0, @cutime=0.0, @stime=4.000000000004e-06, @utime=0.0011600000000000499, @total=0.0011640000000000539>, #<Benchmark::Tms:0x00007fe2fe9ef870 @label="upto: ", @real=0.0006869998760521412, @cstime=0.0, @cutime=0.0, @stime=1.000000000001e-06, @utime=0.0006850000000000467, @total=0.0006860000000000477>]
```

やっていることとしては、以下の３つのプログラムの実行速度を比較しています
- `for i in 1..1000; a = "1"; end`
- `1000.times do ; a = "1"; end`
- `1.upto(1000) do ; a = "1"; end`


benchmarkメソッドの各引数について、
- [第一引数] Benchmark::CAPTION
  - 出力結果の一行目に表示する文字列のことで上記の例でいう[user, system, total, real]がそれにあたります。
- [第二引数] 10
  - ラベルの幅, 出力結果userの前にあるスペースのマス数
- [第三引数] Benchmark::FORMAT
  - このモジュールがデフォルトで提供している実行結果のフォーマット。明示的に指定しなくても上記の例と同じ結果が得られます。

出力結果の意味を以下の表にまとめてみました
| user | system | total | real |
| --- | --- | --- | --- |
| User CPU timeとよばれるもので、 <br> プログラムのコードの実行に費やされた時間のこと。Rubyの処理系が働いた時間。 | System CPU timeとよばれるもので、<br>OSのコードが実行された時間のこと。 | 合計時間(user + system) | 実経過時間 |

以上のことから、
for ~ in, times, uptoの内、**times**を使うといちばん早く繰り返し処理できる

## 参考

https://docs.ruby-lang.org/ja/latest/class/Benchmark.html