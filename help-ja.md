﻿<!--
************************************************************
　こちら側は、ヘルプファイルのソースです。
　目を通す場合は、右側のウィンドウをお読みください。→
************************************************************
-->

<div id='title'>　</div>    

概要
=====

「MarkDown# Editor（マークダウン・シャープ・エディター）」 は、Windows上の日本語環境で動作する、 Markdown記法に対応した軽量なテキストエディターです。

左側にテキストエディター、右側にプレビューするブラウザーを備えた２ペイン式のエディターで、テキストファイルに近い感覚で編集することができ、それを簡単にHTMLファイルを変換することもできます。

また、<a href="http://michelf.ca/projects/php-markdown/extra/" target="_blank" class="external">Markdown Extra</a>にも対応し、tableタグやdlタグなどの編集や、HTMLファイルへの変換が容易になりました。

すでにCSSファイルがある場合や、シンプルな、装飾の少ない小さなWebページの制作に向いています。たとえば、[GitHub](https://github.com)をはじめとしたWebサービスで採用されるMDファイルの作成や、ブログ記事の執筆などでの使用を想定して設計されています。

オープンソースによるフリーソフトウェアとして開発・配布され、商用・個人にかかわらずソースコードを含むすべてをご自由にダウンロードしてお使いいただけます。

最新バージョン、ソースコードなどの詳細情報は、作者サイトにてご確認ください。

HIBARA.ORG   
[http://hibara.org](http://hibara.org)

最新ソースコードはGitHubにあります。   
[https://github.com/hibara/MarkDownSharpEditor](https://github.com/hibara/MarkDownSharpEditor)  
※フォーク、プルリクエスト大歓迎です。

## ヘルプ目次
* [動作環境](#environment)
* [Markdown記法って？](#about)
* [ざっくりとした使い方](#use)
* [開発のキッカケ](#beginning)
* [開発環境](#development)
* [著作権](#copyright)
* [ライセンス](#license)
* [サポート](#support)
* [今後の予定](#upcoming)
* [改版履歴](#history)



<a name="environment"></a>
#動作環境

Windows XP/Vista/7/8、32bit/64bitマシンいずれでも動きます。   
ただし、動作には、.NET Framework 4.0以上が必要です。

インストールされていない場合は、以下のMicrosoftの公式サイトから無償でダウンロードが可能です。

Microsoft .NET Framework 4 (Web インストーラー)    
<a href="http://www.microsoft.com/ja-jp/download/details.aspx?id=17851" target="_blank">
http://www.microsoft.com/ja-jp/download/details.aspx?id=17851</a>

※動作には、Microsoft .NET Framework 4 Client Profile ではなく、**「無印」**の.NET Framework 4が必要です。


##設定ファイル・インストールされるもの

MarkDown#Editorでは、ファイルの関連付けのみレジストリを使っています。そのため、ローカルディレクトリに設定ファイルやサンプルファイル等を作成します。このヘルプファイルなどもインストール時に設置しています。

アンインストーラを使って削除すれば、きれいになりますが、もし手作業などで削除される場合は、以下の辺りにあります。

```C:\Users\[ユーザー名]\AppData\Roaming\MarkDownSharpEditor```



<a name="about"></a>
#Markdown記法って？

Markdown記法について知るには、まず<a href="http://ja.wikipedia.org/wiki/Markdown" target="_blank"  class="external">Wikipedia</a>でしょうか。

さらにMarkdownを策定した人の<a href="http://daringfireball.net/" target="_blank" class="external">サイト</a>（ただし英語）にも詳しく仕様が書いてあります。

また、その仕様ドキュメントを日本語訳されている方のブログ（<a href="http://blog.2310.net/archives/6" target="_blank" class="external">blog::2310</a>）も参考になるかもしれません。

主な用途としては、簡単なWebページを作成したり、ブログ記事などの軽量でシンプルな構造のHTMLソースを書いたりすることに適しています。

最近では、<a href="http://github.com" target="_blank" class="external">GitHub</a> などで採用されていて、ソフトウェア開発上では.md形式のファイルが広まりつつありますが、日本での知名度は今ひとつといった感じでしょうか。

MacではMarkdown記法に対応したエディターがいろいろと見つかるのですが、Windowsとなると意外と見つからなくて、あっても、日本語環境に完全には対応できていないというものでした。

という経緯から、「MarkDown#Editor」を開発してみました。



<a name="use"></a>
#ざっくりとした使い方

Markdown記法を踏まえた上で、左側のウィンドウエリアにMarkdown記法でテキストを入力します。

リアルタイムで右側のウィンドウにプレビューが反映されます。ただ、それだけのシンプルなテキストエディタです。

とはいえ、HTMLファイルとして出力できるのはもちろんのこと、クリップボードにHTMLソースとして保存することも１クリックでいけます。

また、HTML出力にあたっては、CSS埋め込みから、外部リンキングなど、さまざまな出力オプションを選択できます。

「MarkDown# Editor」 にはあらかじめ登録されたCSSファイルがいくつかありますが、自分で用意したCSSファイルを追加して表示することもできます。

プリインストールされたCSSファイルの種類は、まだまださみしい感じですが（徐々に増やしてはいこうと思いますが）、ネットにいろいろとサンプルは落ちていそうですので、拾ってきてインポートなどしてお使いください。


##相対パスと絶対パス

基本的にテキストエリアに書いた相対パス（例 image/hoge.png）は、現在書かれているMDファイルのある場所を基点にファイルを探しに行きます。

そのため、画像やその他ファイルへのリンクを書きながら確認したいという場合は、同じフォルダにそれらのリソースデータファイルを持ってきておく必要があります。

それが不便だ、という場合は、あからじめご自身のブログにイメージをアップロードしておいて、絶対パスを書かれた方が良いかもしれません。

例として次の画像は、外部URLでの指定です。


![外部URLのアイコン](http://hibara.org/software/markdownsharpeditor/img/main_icon_48x48.png)   


ただ、当然ですが、表示にはネット接続された環境になっていないといけません。ネット未接続だと、上記の画像は正常に表示されないはずです。

<a name="beginning"></a>
#開発のキッカケ

もともと僕は「<a href="http://hibara.org/software/attachecase/"  target="_blank" class="external">アタッシェケース</a>」という暗号化ソフトウェアの開発を行っていますが、ヘルプファイルを刷新するにあたって、Markdown で書こうと思い立ちました。ところが、いざツールを探してみると、日本語環境のWindows上で使えるものがほとんどありませんでした。

Macには、その手のエディターを多く見つけられるのですが、意外にもWindowsで、日本語対応したものがなかったので、サクッとつくってみました（でもけっきょくは重い作業だった・・・(笑)）。



<a name="development"></a>
#開発環境

開発には、VisualStudio C# 2010 Express を使用しています。

Markdown記法のパーサーには、次の「著作権」の項目にある、C#にインプリメントされたクラスライブラリを使わせてもらいました。BSDライセンスということで、下記にすべて著作権表示されています（ソフトウェア内のバージョン情報にも記載してあります）。

また、開発者で興味がある方は、下記のURLをそれぞれ訪れていただければ、ドキュメントやライブラリを入手されると良いでしょう。



<a name="copyright"></a>
#著作権

## Markdown  -  A text-to-HTML conversion tool for web writers   
Copyright (c) 2004 John Gruber   
[http://daringfireball.net/projects/markdown/](http://daringfireball.net/projects/markdown/)   

## MarkdownDeep
[http://www.toptensoftware.com/markdowndeep/](http://www.toptensoftware.com/markdowndeep/)
Copyright 2010-2011 Topten Software

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this product except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.



<a name="license"></a>
#ライセンス

GPLv3を適用します。ただし、前項にある使用しているライブラリなどを単体で使用する場合は、各作者のライセンスに従ってください。

「MarkDown#Editor」に限っていえば、ライセンス条項に同意していただければ、商用・私用にかかわらずソースコードを含むすべてを基本的には無償でお使いいただけます。

詳細は以下からご確認いただけます。   
https://www.gnu.org/licenses/gpl-3.0.html

※参考（上記の和訳）   
http://ossipedia.ipa.go.jp/legalinfo/gpl-3.0J.html

本ソフトウェアの使用、改変、再頒布、販売などは、上記のライセンスに従ってください。この件に関して作者への問い合わせはなるべくお控えください（忙しいもので）。



<a name="support"></a>
#サポート

作者多忙につき、なかなか返信することができませんが、その点だけご容赦ください。

些細な質問などは、どうかご勘弁を（たぶん返信することはないでしょう）。

ただ、「この機能がほしい」「これってバグでは？」といったフィードバックやご報告は大歓迎です。

その場合は、こちらからどうぞ。  
https://github.com/hibara/MarkDownSharpEditor/issues

ややレスポンスは鈍いかもしれませんが、メールでも受け付けています。  
その場合は、こちらからどうぞ。

ひばら　みつひろ   
<m@hibara.org>



<a name="upcoming"></a>
#今後の予定

まだまだ機能は十分ではありませんが、ユーザーさんのご意見をうかがいながら、ちょっとずつ整えていこうと思います。将来的には、出力ファイルをサーバーにデプロイするところまで、とか。そこまでいくと、ちょっと難易度上がるかな‥‥。

その前にもう少し表示のパフォーマンスを上げることですかね。。。

現状では、特にバグのご報告や、プリインストールのCSSファイルのご提供など、絶賛お待ちしています。

また、オープンソース化しておりますので、GitHub上でのフォークや、プルリクエストなど開発者側でのフォロー大募集。


<a name="history"></a>
#改版履歴

##ver.1.2.3.0　　2013/10/22

* ブラウザプレビューが更新されるたびにフォーカスが失われて編集がしにくい問題に対処(※1)。

* 既存の .md ファイルを開いて、何も変更せずに保存すると開いた .md ファイルが削除されてしまう問題に対処(※2)。

* 前回いただいたプルリクエスト（シンタックスハイライターの処理周り）がきちんとソース、及びプログラムに反映されていなかったものを改めて反映。

* インストール時に選択した言語設定（英語 or 日本語）で、起動するように改良。

	※1,2:[kkato233](https://github.com/kkato233)さん、katoさんご指摘と修正、また、プルリクエストありがとうございました！


##ver.1.2.2.0　　2013/06/27

* 動作設定パネルで、CSSファイルをドラッグ＆ドロップで登録できるようした。また、ファイル選択ダイアログからも、複数ファイルを選択可能にして、まとめて登録できるようにした。

* 終了時にブラウザー描画が行われていたとき、強制終了してしまう問題に対処。

* 「ファイルを開く」を選択すると、新規ファイルの動作になっていた不具合。

* 表組みの背景色が正常に保存できていなかった問題に対処。

* インストール後の初期起動で、日本語ヘルプファイルを開くときに、意図しないCSSが適用されていた問題に対処。

* シンタックスハイライター処理でバックスラッシュエスケープの正規表現に誤りがあるなど、その他パフォーマンスを改善。(※1)

* ブラウザープレビューでヘルプファイルが開けないなど、表示処理にいろいろ問題を抱えていたのを修正。(※2)

	※1, 2: いずれも、[Yasami](https://github.com/Yasami)さん、プルリクエストありがとうございました！


##ver.1.2.1.0　　2013/06/18

* 最新バージョンをチェックするメニューを追加。

* 一部のダイアログ表示でメッセージが表示されていなかった問題（ローカライズの問題）に対処。

* 新しく編集を開始するとクラッシュしてしまう致命的な問題に対処。

* 編集中に文章の末端に到達すると、同様にクラッシュしてしまうことがあった問題に対処。

* 編集中にIMEが確定してしまう問題に対処（日本語環境上で動作させているときのみ確定しないように改良）。

* 日本語環境でインストーラを実行したときも、英語版として初回起動してしまっていた不具合に対処。


##ver.1.2.0.0　　2013/06/09

* Markdown Extra モードに対応。

* 英語版作成に伴って国際化（多言語化）対応。

* エディター側のシンタックスハイライト処理が重たくなってきたので、編集された前後の範囲のみ、適用するように改良。

* ブラウザプレビューをBackgoundWorkerで処理（別スレッドで処理）することにした。

* 動作設定の「ブラウザプレビューまでの間隔」設定を行うとエラーが発生していた問題に対処。


##ver.1.1.5.0　　2013/03/07

* 「新規作成」や無題で編集を開始したとき、編集ウィンドウでスクロールさせようとするとエラーが発生してした不具合に対処。

* 「新規作成」を行っていると、「無題[0001].md」といったテンポラリファイルをローカルパスに作成し続けてしまう不具合に対処。

* 内部的な編集履歴（mdファイルと、cssファイルのセット）の数が、一定数（現状20に設定してます）を超えてしまうと、終了時にエラーが発生していた不具合に対処。

* 文字列検索・置換で「すべてを置換する」を選択したとき、置換文字列を入力し続けてしまい、暴走してしまうことがあった不具合に対処。

* 半角スペースを含むMDファイルなど、関連付け起動がうまく機能していなかった不具合に対処。

* 動作設定の「全般」で、「ブラウザープレビューまでの間隔」で、ある操作を行うとデバッグモードが作動し、テキストボックスの入力方式になってしまっていた不具合に対処。

* ブラウザプレビューが行われるタイミングでMarkDown#Editorを終了したとき、まれにエラーが発生していた不具合に対処（プレビュー処理に行くスレッドをきちんと止めてから終了するようにした）。

* エディター側のスクロール挙動を微調整。


##ver.1.1.4.0　　2013/01/30

* ブラウザーウィンドウを更新するときのクリック音を処理するところで強制終了していた不具合に対処（内部的に別のアプローチでクリック音を消去するようにした）。

* ウィンドウ全般の前景と背景色の設定項目を追加した（内部的に設定項目はあったのですが、UIの方を作るのを忘れていました・・・）


##ver.1.1.3.0　　2012/12/25

* 検索・置換機能を新規に追加。

* ウィンドウを「最小化」「最大化」していた場合に、正確にフォーム位置・サイズを保存していなかったので改良。

* クリップボードにHTMLソース出力のアイコンが、ファイル出力と区別がつかず、わかりにくかったのでデザインを微修正。

* ウェブブラウザーコンポーネントの更新イベントが起きる度にカチカチ言っていたサウンドをMarkDown#Editor起動中はOFFにするようにした。

* 登録されたビルトインCSSファイルが存在しない場合にも、ステータスバーのCSSファイルを選択するポップアップメニューが表示されていた不具合に対処。


##ver.1.1.2.0　　2012/12/12

* 「見出し記号へのジャンプリスト表示」機能をメニューに新規追加。

* シンタックスハイライターで使っている正規表現では、Markdown記法の「見出し記号（h1～h6）」を正しく解釈できない場合があった不具合に対処。


##ver.1.1.1.0　　2012/12/11

* 新規作成でファイルを編集しはじめると、強制終了するという致命的な不具合に対処（すみません・・・前回修正の縁バグです）。

* マーカー表示周りの改良に伴い、エディター側で編集していた内容の一部が、右側のブラウザプレビューに表示されていなかった不具合に対処。


##ver.1.1.0.0　　2012/12/07

* エディタ部分のテキストフォント変更ができないという[プルリクエスト](https://github.com/hibara/MarkDownSharpEditor/pull/1)を受けたのでマージした。（[alg](https://github.com/alg0002)さん、プルリクエストありがとうございました！）

* また、それに関連して、日本語表示できないフォント表示するとテキストが壊れて、元のフォントに戻せなくなるため（正確には復元できない）、フォント変更もUndoバッファに入れて、「元に戻す」コマンドで戻せるようにした。

* ファイルを開くダイアログのデフォルトファイル名に「openFileDialog1」というコンポーネント名が入っていたので削除したのと、現在編集中のファイルがあれば、その場所を初期ディレクトリとして開くように改良。

* 新規作成の状態から、見出し文字を編集していくとブラウザー側にゴミ表示が増えていき、消すことができない問題に対処。

* 編集途中でファイルを読み込み、「元に戻す」コマンド実行すると強制終了してしまう不具合に対処（※1）。

* 内容を編集時にブラウザプレビューが更新されても、表示位置（スクロールバー位置）を保つように改良（※2）。
（※1, ※2 [mattnさん](https://github.com/mattn)、ご指摘＆修正サンプルソースをありがとうございました！）

* テキストエディターと、ブラウザプレビューのスクロール追従周りを大幅に手を入れ、改良した。また、編集中におけるプレビューやシンタックスハイライターの処理を微調整した（編集中の重い引っかかりなどが心なしか軽減されたかと思います・・・）。


##ver.1.0.9.0　　2012/10/31

* オープンソース化に伴うヘルプファイルの書き換えや、ソースコード（主にコメントアウトなど直接的な動作とは関係ないところ）の修正。


##ver.1.0.8.0　　2012/10/16

* 新しいCSSファイルを追加してもポップアップメニューや、デフォルトCSSとして設定することができなかった不具合に対処。

* Markdownの「リスト」表示において、「リスト記号の前にスペース３つまで許す」「記号の後にタブまたはスペースを**１以上**」という仕様がシンタックスハイライトに反映されていなかった不具合に対処。

* 数字ではじまる「リスト」のシンタックスハイライトに対応していなかった不具合に対処。

* 編集途中に「リスト」が混じると、正しく編集箇所のマークが表示されなかったり、プレビューウィンドウのスクロールが追従していなかった不具合に対処。


##ver.1.0.7.0　　2012/10/02

* 出力されるHTMLソースに、<body>タグが含まれていなかったという凡ミスに対処（すみません・・・）。

* テキストエディター側のスクロールと、ブラウザプレビューウィンドウのスクロールを同期するように改良。

* テキストエディター側のカーソルが移動する度にブラウザー描画していたのを省略し、少しだけチラつきを抑えるようにした。また、時間差でマーキングするようにして誤魔化した(笑)。

* 読み込んだブラウザーページのエンコーディング表示が正しく反映されていなかった不具合に対処。

* 動作設定を変更したとき、即座にメインウィンドウに反映していなかった不具合。

* ブラウザー側の編集箇所のカラー表示のON/OFF設定が正しく反映されていなかった不具合に対処。

* HTMLファイルに関連付けされたブラウザーを起動してプレビューする機能をツールバーとメニューに追加。

* 編集中においても、意図的に反映のラグをつくって無駄な描画回数を減らすように調整した（※次の項目と少し絡みます）。

* ブラウザープレビューの間隔を秒単位で調整できるようにして、かつ、自動更新せずに手動で更新する設定も新たに追加した。

* CSS設定リストの一番上に登録されたファイルを「デフォルト」のCSSファイル設定とする機能の追加。

* 「無題」ファイルの編集する度に、一時ファイルを生成し続けるという不具合に対処。むしろ逆に、「無題」で編集中は一時ファイルとして書き出さないようにした（そのため、無題のまま編集するとリンクなどが正しく動作しないことがあります。それは「仕様」としました。）


##ver.1.0.6.0　　2012/09/23

* ローカルに指定された画像（相対パス画像）が、最初にロードされたときには表示されるが、編集途中で表示されなくなる不具合に対処。

* エディタ冒頭にある「見出し」などを変更すると、シンタックス・ハイライター表示がテキスト全体に適用されてしまう不具合に対処。

* 新しくファイルを開いたときに、シンタックス・ハイライターのパース処理が走らなかった不具合に対処。

* 書式のあるテキストをコピー＆ペーストすると、エラーが発生していたことがあった問題に対処。

* Undo, Redoともに正常に動作していなかった不具合に対処。


##ver.1.0.5.0　　2012/09/18

* エディターのシンタックス・ハイライター処理を行ったとき、元のフォント設定が失われる不具合に対処。

* 関連付けファイルからの起動が機能していなかった不具合を修正。

* 「最近開いたファイル」からファイルパスを選んでもファイルを開けていなかった不具合に対処。

* テキストエディタ側で別ファイルを読み込み直すなどしたときに、きちんとシンタックスハイライターをクリアしていなかった不具合に対処。


##ver.1.0.4.0　　2012/09/11

* エディター側のシンタックス・ハイライターを実装した。ただ、けっこう重いので、ある程度の負荷分散処理も入れてみました。不完全な部分があればご一報くださると助かります。

* Webブラウザのプレビュータイミングを調整して、体感的な表示速度と負荷のバランスをとった。

* Webブラウザのプレビューウィンドウに「更新」「中止」ボタンの追加。

* フォームのタイトルのファイル名をフルパス表示に変更。

* フォームへのファイルのドラッグ＆ドロップが機能しなくなっていた不具合に対処。


##ver.1.0.3.0　　2012/09/08

* CSSファイルの登録ができなかったり、設定が保存されない、また削除するときに強制終了するなどのCSS設定パネル周りを修正（ぼろぼろで、ごめんなさい‥‥）

* ブラウザー表示に「戻る」「進む」ボタンを追加した。何度も更新が入ると、動作速度に影響があるので、頻繁には履歴を更新していません（保存したときにナビゲートしていますので、ページ履歴がそのとき作られ、戻る・進むが可能になります）。

* 実験的にエディターウィンドウの方のシンタックス・ハイライター機能を追加。動作速度をみたいので、とりあえず一番わかりにくい「行末の半角スペース×2（＝強制改行）のところの背景色だけ変えられるようにした。


##ver.1.0.2.0　　2012/09/06

* HTMLファイル出力で、二重にヘッダーやフッターが挿入されることがあった不具合に対処。

* 「無題」のファイルを編集すると、強制終了していた不具合に対処。

* 複数ファイルをまとめてドラッグ＆ドロップすると、現在設定で一括処理する機能を追加した。


##ver.1.0.1.0　　2012/09/05

* HTMLソースのクリップボード保存で強制終了していた不具合に対処。

* カーソルが動いたり、少しでも編集するとプレビューページがカチカチと音を立てていたのを改善。内部的に言えば、毎回Navigate()を呼んでいたのを極力呼ばずに中身を再描画するようにした。      

* ファイルを保存したのに「更新」状態が解除されない不具合に対処（ファイルを閉じるときに変更された旨の通知が出てしまっていた）。


##ver.1.0.0.0　　2012/09/02

* 公開



---
Copyright&copy; 2012-2013 M.Hibara, All rights Reserved. 
