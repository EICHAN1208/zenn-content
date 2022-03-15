---
title: "RailsのPlugin・RubyのGem"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["test"]
published: true
---

## RailsのPluginとは
Railsというフレームワークの拡張機能のこと。
Pluginとしてソースコードを切り出すことで開発者感での共有がしやすくなったり、独立して実装を進めることができるというところに良さがあり、Railsがもつ標準機能を活かすことを前提に実装されたものです。

## GemとPluginの違い
GemはRubyGemsで定義されたパッケージングシステムを使用してパッケージ化されたRubyアプリケーションのことで、PluginはRailsというフレームワークに組み込まれた拡張機能であると理解しました。

Railsフレームワーク自体もGemであり、このRails自体に組み込まれるPluginもgemとして共有することができる。Gem(Rails)に組み込まれたGem(Plugin)ということが言えそうです。

使い分けの方法としては、**汎用的なRubyスクリプトをGem化したいときはシンプルなRubyのGemとして作成し、Railsのレールに乗ってGemを作成したい場合(Railsの標準機能を使用したい場合)はPluginを作成する**という使い分けで良いのではないかと思っています。

## 参考
https://guides.rubyonrails.org/plugins.html
https://stackoverflow.com/questions/5521224/difference-between-plugins-and-ruby-gems/5521244#5521244
