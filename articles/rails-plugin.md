---
title: "RailsのPluginについて"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["test"]
published: false
---

# RailsのPluginとは
Railsというフレームワークの拡張機能。
Pluginとしてソースコードを切り出すことで開発者感での共有がしやすくなったり、独立して実装を進めることができるというところにメリットがあります。

# GemとPluginの違い・使い分け
GemはRubyGemsで定義されたパッケージングシステムを使用してパッケージ化されたRubyアプリケーションのことで、PluginはRailsというフレームワークに組み込まれた拡張機能であると思っています。

使い分けの方法としては、汎用的なRubyスクリプトをGem化したいときはシンプルなRubyのGemとして作成し、Railsのレールに乗ってGemを作成したい場合はPluginを作成するという使い分けで良いのではと思っています。

Railsフレームワーク自体もGemであって、このRailsに組み込まれるPluginもgemとして共有することができる。
つまり、Gem(Rails)に組み込まれたGem(Plugin)ということが言えそうです。ややこしい。

# 参考
https://guides.rubyonrails.org/plugins.html
https://stackoverflow.com/questions/5521224/difference-between-plugins-and-ruby-gems/5521244#5521244


