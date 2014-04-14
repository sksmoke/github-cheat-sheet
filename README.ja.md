# GitHubカンニング・ペーパー

これはGitやGitHubの隠された機能やよく知られていない機能の一覧だ。[Zach Holman](https://github.com/holman)によるAloha Ruby Conference 2012での[Git and GitHub Secrets](https://github.com/tiimgreen/github-cheat-sheet)（[スライド](https://github.com/tiimgreen/github-cheat-sheet)）とWDCNZ 2013での[More Git and GitHub Secrets](https://vimeo.com/72955426)（[スライド](https://speakerdeck.com/holman/more-git-and-github-secrets)）の二つのトークを元にしている。

# 目次

- [空白の無視](#%E7%A9%BA%E7%99%BD%E3%81%AE%E7%84%A1%E8%A6%96)
- [リポジトリのクローン](#%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%81%AE%E3%82%AF%E3%83%AD%E3%83%BC%E3%83%B3)
- [Hub - Gitラッパー](#hub---git%E3%83%A9%E3%83%83%E3%83%91%E3%83%BC)
- [共同開発者との摩擦の軽減](#%E5%85%B1%E5%90%8C%E9%96%8B%E7%99%BA%E8%80%85%E3%81%A8%E3%81%AE%E6%91%A9%E6%93%A6%E3%81%AE%E8%BB%BD%E6%B8%9B)
- [直前のブランチ](#%E7%9B%B4%E5%89%8D%E3%81%AE%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81)
- [Git.io](#gitio)
- [Gists](#gists)
- [キーボード・ショートカット](#%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89%E3%82%B7%E3%83%A7%E3%83%BC%E3%83%88%E3%82%AB%E3%83%83%E3%83%88)
- [コミットからイシューを閉じる](#%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%81%8B%E3%82%89%E3%82%A4%E3%82%B7%E3%83%A5%E3%83%BC%E3%82%92%E9%96%89%E3%81%98%E3%82%8B)
- [プルリクエストのチェックアウト](#%E3%83%97%E3%83%AB%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%81%AE%E3%83%81%E3%82%A7%E3%83%83%E3%82%AF%E3%82%A2%E3%82%A6%E3%83%88)
- [イシューの相互リンク](#%E3%82%A4%E3%82%B7%E3%83%A5%E3%83%BC%E3%81%AE%E7%9B%B8%E4%BA%92%E3%83%AA%E3%83%B3%E3%82%AF)
- [開発参加のガイドライン](#%E9%96%8B%E7%99%BA%E5%8F%82%E5%8A%A0%E3%81%AE%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3)
- [Markdownファイルでの構文強調](#markdown%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%A7%E3%81%AE%E6%A7%8B%E6%96%87%E5%BC%B7%E8%AA%BF)
- [特定のユーザーによるコミット履歴](#%E7%89%B9%E5%AE%9A%E3%81%AE%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC%E3%81%AB%E3%82%88%E3%82%8B%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E5%B1%A5%E6%AD%B4)
- [空のコミット :trollface:](#%E7%A9%BA%E3%81%AE%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88)
- [ブランチ同士の比較](#%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81%E5%90%8C%E5%A3%AB%E3%81%AE%E6%AF%94%E8%BC%83)
- [コードの指定行の強調](#%E3%82%B3%E3%83%BC%E3%83%89%E3%81%AE%E6%8C%87%E5%AE%9A%E8%A1%8C%E3%81%AE%E5%BC%B7%E8%AA%BF)
- [GitHub Pagesでのメタデータとプラグインのサポート](#github-pages%E3%81%A7%E3%81%AE%E3%83%A1%E3%82%BF%E3%83%87%E3%83%BC%E3%82%BF%E3%81%A8%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%E3%81%AE%E3%82%B5%E3%83%9D%E3%83%BC%E3%83%88)
- [差分の表示](#%E5%B7%AE%E5%88%86%E3%81%AE%E8%A1%A8%E7%A4%BA)
  - [レンダリング済みの差分](#%E3%83%AC%E3%83%B3%E3%83%80%E3%83%AA%E3%83%B3%E3%82%B0%E6%B8%88%E3%81%BF%E3%81%AE%E5%B7%AE%E5%88%86)
  - [マップ差分の可視化](#%E3%83%9E%E3%83%83%E3%83%97%E5%B7%AE%E5%88%86%E3%81%AE%E5%8F%AF%E8%A6%96%E5%8C%96)
  - [差分表示の前後を表示](#%E5%B7%AE%E5%88%86%E8%A1%A8%E7%A4%BA%E3%81%AE%E5%89%8D%E5%BE%8C%E3%82%92%E8%A1%A8%E7%A4%BA)
- [Emoji](#emoji)
- [画像及びアニメーションGIF](#%E7%94%BB%E5%83%8F%E5%8F%8A%E3%81%B3%E3%82%A2%E3%83%8B%E3%83%A1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3gif)
  - [GitHub Wikiへの画像の添付](#gitHub-wiki%E3%81%B8%E3%81%AE%E7%94%BB%E5%83%8F%E3%81%AE%E6%B7%BB%E4%BB%98)
- [素早く引用](#%E7%B4%A0%E6%97%A9%E3%81%8F%E5%BC%95%E7%94%A8)
- [Gitステータスのスタイリング](#git%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9%E3%81%AE%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AA%E3%83%B3%E3%82%B0)
- [Gitログのスタイリング](#git%E3%83%AD%E3%82%B0%E3%81%AE%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AA%E3%83%B3%E3%82%B0)
- [コミットログの検索](#%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E3%83%AD%E3%82%B0%E3%81%AE%E6%A4%9C%E7%B4%A2)
- [マージ済みブランチ](#%E3%83%9E%E3%83%BC%E3%82%B8%E6%B8%88%E3%81%BF%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81)
- [設定済みライセンスの追加](#%E8%A8%AD%E5%AE%9A%E6%B8%88%E3%81%BF%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9%E3%81%AE%E8%BF%BD%E5%8A%A0)
- [タスクリスト](#%E3%82%BF%E3%82%B9%E3%82%AF%E3%83%AA%E3%82%B9%E3%83%88)
- [相対リンク](#%E7%9B%B8%E5%AF%BE%E3%83%AA%E3%83%B3%E3%82%AF)
- [推奨したい`.gitconfig`](#%E6%8E%A8%E5%A5%A8%E3%81%97%E3%81%9F%E3%81%84gitconfig)
  - [エイリアス](#%E3%82%A8%E3%82%A4%E3%83%AA%E3%82%A2%E3%82%B9)
  - [コマンドの自動修正](#%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E8%87%AA%E5%8B%95%E4%BF%AE%E6%AD%A3)
  - [色設定](#%E8%89%B2%E8%A8%AD%E5%AE%9A)

## 空白の無視

GitHub上で差分ページを表示している時、そのURLに`?w=1`を加えると、空白の変化によるできた差分は表示されなくなり、コード上の変化だけを参照することができる。

[*GitHubの秘密についてもっと詳しく*](https://github.com/blog/967-github-secrets)

## リポジトリのクローン

リポジトリをクローンする時、URLの末尾の`.git`は無くても構わない。

```bash
$ git clone https://github.com/tiimgreen/github-cheat-sheet
```

[*Gitの`clone`コマンドについてもっと詳しく*](http://git-scm.com/docs/git-clone)

## Hub - Gitラッパー

[Hub](https://github.com/github/hub)はGitのラッパーとして機能するコマンドライン・ツールで、これを利用するとGitHubをコマンドラインからとても簡単に扱えるようになる。

例えば以下のようにしてリポジトリのクローンが行える:

```bash
$ hub clone tiimgreen/toc
```

これが以下のコマンドの代わりというわけだ:

```bash
$ git clone https://github.com/tiimgreen/toc.git
```

[*Hubが提供する便利な機能についてもっと詳しく*](https://github.com/github/hub#commands)

## 共同開発者との摩擦の軽減

もし誰かに自分のプロジェクトの利用またはその開発に参加してもらいたい場合、まずはよくある質問に答えることから始めなければならないだろう。このプロジェクトはどういうものなのか？どうやって使うのか？どのように使っても良いのか？どうやれば開発に参加できるのか？どうやれば開発環境を用意できるのか？どうやって自分の加えた機能が既存の機能を破壊しないことが確認できるのか？

[Friction](https://github.com/rafalchmiel/friction)はこういった[一般的な質問に対しての答え](https://github.com/rafalchmiel/friction/wiki)が用意されているかをチェックしてくれるコマンドライン・ツールだ。例えば以下のような出力を得られる:

[![Friction output](http://i.imgur.com/4EgpWo4.png)](https://github.com/rafalchmiel/friction)

## 直前のブランチ

コマンドラインで直前にいたディレクトリへ移動するには以下のようにすれば良い:

```bash
$ cd -
```

同じようにGitで直前のブランチをチェックアウトすることができる:

```bash
$ git checkout -
# Switched to branch 'master'

$ git checkout -
# Switched to branch 'next'

$ git checkout -
# Switched to branch 'master'
```

[*Gitのブランチ操作についてもっと詳しく*](http://git-scm.com/book/en/Git-Branching-Basic-Branching-and-Merging)

## Git.io

[Git.io](http://git.io)はGitHubの提供するGitHub専用のシンプルな短縮URLサービスだ。cURLを使って利用することができる:

```bash
$ curl -i http://git.io -F "url=https://github.com/..."
HTTP/1.1 201 Created
Location: http://git.io/abc123

$ curl -i http://git.io/abc123
HTTP/1.1 302 Found
Location: https://github.com/...
```

[*Git.ioについてもっと詳しく*](https://github.com/blog/985-git-io-github-url-shortener)

## Gists

[Gists](https://gist.github.com/)は少量のコード群を管理する最適な手段だ。ちゃんとしたリポジトリをいちいち作成する必要はない。GistのURLの最後に`.pibb`を付ける([例](https://gist.github.com/hail2u/9477708.pibb))と*HTMLのみ*のバージョンが表示されるので、そのソースは他のウェブサイトに貼り付けるにはもってこいだろう。

簡単なものとはいえ、完全なGitリポジトリとして機能するため、以下のようにすれば普通のGitリポジトリと同じようにクローンすることができる:

```bash
$ git clone https://gist.github.com/tiimgreen/10545817
```

![Gists](http://i.imgur.com/dULZXXo.png)

[*Gistの作成についてもっと詳しく*](https://help.github.com/articles/creating-gists)

## キーボード・ショートカット

リポジトリをブラウザーで開いている時は、ショートカットを利用して様々な機能ヘ簡単にアクセスできるようになっている。

`t`を押すとファイルの検索インターフェイスが起動する。

`w`を押すとブランチ選択インターフェイスが起動する。

`s`を押すとコマンド・バーにフォーカスが当たる。

イシュー画面で`l`を押すとラベルの編集インターフェイスが開かれる。

__ファイルを参照している時__（例: `https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.md`)に`y`を押すと、参照している時の状態で固定されるURLに変更される。つまりそのファイルのコードが後に変化したとしても、そのURLでは今とまったく同じ状態で表示されるということだ。

`?`を押すとそのページで使える全ショートカットが表示されるだろう。

[*コマンドバーについてもっと詳しく*](https://help.github.com/articles/using-the-command-bar)

## コミットからイシューを閉じる

あるコミットでイシューを解決した場合、コミットメッセージで`fix/fixes/fixed`または`close/closes/closed`に続けてイシュー番号を指定すると、そのコミットがmasterブランチにpushされると同時に指定イシューが閉じられるだろう。

```bash
$ git commit -m "Fix cock up, fixes #12"
```

こうするとイシュー#12が閉じられ、閉じたイシューにはそのコミットへの参照が自動的に追加される。

![Closing Repo](http://i.imgur.com/URXFprQ.png)

[*コミット・メッセージからイシューを閉じる方法についてもっと詳しく*](https://help.github.com/articles/closing-issues-via-commit-messages)

## プルリクエストのチェックアウト

プルリクエストをローカル・リポジトリへチェックアウトするには、まず以下のようにコマンドを実行しその変更を取り込む:

```bash
$ git fetch origin '+refs/pull/*/head:refs/pull/*'
```

そして、プルリクエストを番号（例: 42）を指定してチェックアウトする:

```bash
$ git checkout refs/pull/42
```

別の方法としては、まずプルリクエストをリモート・ブランチとして取り込み:

```bash
$ git fetch origin '+refs/pull/*/head:refs/remotes/origin/pr/*'
```

それから番号を指定して取り込むこともできる:

```bash
$ git checkout origin/pr/42
```

またプルリクエストの取り込みは、.git/configに以下の行を追加すると自動化することができる:

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
```

```
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = git@github.com:tiimgreen/github-cheat-sheet.git
    fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```

[*プルリクエストのチェックアウトについてもっと詳しく*](https://help.github.com/articles/checking-out-pull-requests-locally)

## イシューの相互リンク

同じリポジトリの違うイシューへリンクを張り参照させたい場合、`#`に続けてイシュー番号を指定する。そうすると自動的にリンクが作成されるだろう。

別のリポジトリのイシューの場合は`user_name/repo_name#ISSUE_NUMBER`とすれば良い（例: `tiimgreen/toc#12`）。

![Cross-Link Issues](https://camo.githubusercontent.com/447e39ab8d96b553cadc8d31799100190df230a8/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f626c6f672f323031312f736563726574732f7265666572656e6365732e706e67)

## 開発参加のガイドライン

リポジトリのルートに`CONTRIBUTING`という名前のファイルを置くと、イシューやプルリクエストを作成しようとした時にそれへのリンクが表示されるようになる。

![Contributing Guidelines](https://camo.githubusercontent.com/71995d6b0e620a9ef1ded00a04498241c69dd1bf/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f736b697463682f6973737565732d32303132303931332d3136323533392e6a7067)

[*開発参加のガイドラインについてもっと詳しく*](https://github.com/blog/1184-contributing-guidelines)

## Markdownファイルでの構文強調

例えばMarkdownファイルでRubyのコードを構文強調したいならば以下のようにする:

    ```ruby
    require 'tabbit'
    table = Tabbit.new('Name', 'Email')
    table.add_row('Tim Green', 'tiimgreen@gmail.com')
    puts table.to_s
    ```

こうすると以下のように表示されることになる:

```ruby
require 'tabbit'
table = Tabbit.new('Name', 'Email')
table.add_row('Tim Green', 'tiimgreen@gmail.com')
puts table.to_s
```

GitHubでは[Linguist](https://github.com/github/linguist)を使って言語を判別し構文強調を行っている。構文強調がサポートされている言語の一覧は[言語定義YAMLファイル](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)を参照すればわかるだろう。

[*GitHub Flavored Markdownについてもっと詳しく*](https://help.github.com/articles/github-flavored-markdown)

## 特定のユーザーによるコミット履歴

特定のユーザーによるあるリポジトリへのコミット履歴のみを参照したい場合は、`?author=username`をURLの末尾に付ける。

```
https://github.com/rails/rails/commits/master?author=dhh
```

[*コミット・ビューの違いについてもっと詳しく*](https://help.github.com/articles/differences-between-commit-views)

## 空のコミット :trollface:

`--allow-empty`オプションを付けると、コードの変化がなくてもコミットを作成することができる:

```bash
$ git commit -m "Big-ass commit" --allow-empty
```

## ブランチ同士の比較

GitHubのブランチ比較は以下のようなURLで提供されている:

```
https://github.com/user/repo/compare/{range}
```

例えば`{range}`を`master...4-1-stable`に変更して利用する:

```
https://github.com/rails/rails/compare/master...4-1-stable
```

`{range}`には以下のように日付け指定を利用することもできる:

```
https://github.com/rails/rails/compare/master@{1.day.ago}...master
https://github.com/rails/rails/compare/master@{2014-10-04}...master
```
masterブランチと特定の期間または日時との比較が行えるだろう。

[*時間を指定してのブランチ比較についてもっと詳しく*](https://help.github.com/articles/comparing-commits-across-time)

### フォークされたリポジトリ間でのブランチ比較

GitHubでフォークされたリポジトリ同士でブランチを比較する場合、以下のようなURLを変更する:

```
https://github.com/user/repo/compare/{foreign-user}:{branch}...{own-branch}
```

例:

```
https://github.com/rails/rails/compare/byroot:idempotent-counter-caches...master
```

## コードの指定行の強調

コードのURLの末尾に`#L52`と付けるか行番号をクリックすると、その行が強調表示される。

これは範囲指定も可能だ（例: `#L53-L60`）。こういった範囲を選択するには`shift`を押しながら二つの行をクリックしても良い:

```
https://github.com/rails/rails/blob/master/activemodel/lib/active_model.rb#L53-L60
```

![Line Highlighting](http://i.imgur.com/8AhjrCz.png)

## GitHub Pagesでのメタデータとプラグインのサポート

Jekyllのページや投稿ではリポジトリの情報が`site.github`という名前空間に格納されており、例えば`{{ site.github.project_title }}`などと書けば表示することができる。

The Jemoji and jekyll-mentions plugins enable [emoji](#emojis) and [@mentions](https://github.com/blog/821) in your Jekyll posts and pages to work just like you'd expect when interacting with a repository on GitHub.com.
また、Jemojiとjekyll-mentionsというプラグインがインストールされているので、[Emoji](#emoji)や[@mentions](https://github.com/blog/821)はJekyllの投稿やページでGitHub.com上と同じように動作する。

[*GitHub Pageでのメタデータとプラグインのサポートについてもっと詳しく*](Repository metadata and plugin support for GitHub Pages)

## 差分の表示

### レンダリング済みの差分表示

Commits and pull requests including rendered documents supported by GitHub (e.g. Markdown) feature *source* and *rendered* views.
コミットやプルリクエストにGitHubでレンダリングされて表示されるもの（例: Markdown）が含まれる場合、その*ソース*と*レンダリング済み*の両方の差分を見ることができる。

![Source / Rendered view](https://github-images.s3.amazonaws.com/help/repository/rendered_prose_diff.png)

レンダリングされた状態での差分を表示したい場合は「Rendered」ボタンをクリックする。レンダリング済みの差分表示では文章の追加や削除、編集がよりわかりやすい:

![Rendered Prose Diffs](https://f.cloud.github.com/assets/17715/2003056/3997edb4-862b-11e3-90be-5e9586edecd7.png)

[*レンダリング済みの差分表示についてもっと詳しく*](https://github.com/blog/1784-rendered-prose-diffs)

### マップ差分の可視化

コミットやプルリクエストにジオデータの変更が含まれている場合はいつも、GitHubではそのジオデータの変化を可視化してくれるだろう。

[![Diffable Maps](https://f.cloud.github.com/assets/282759/2090660/63f2e45a-8e97-11e3-9d8b-d4c8078b004e.gif)](https://github.com/benbalter/congressional-districts/commit/2233c76ca5bb059582d796f053775d8859198ec5)

[*マップ差分の可視化についてもっと詳しく*](https://github.com/blog/1772-diffable-more-customizable-maps)

### 差分表示の前後を表示

差分表示の行番号付近にある*展開*ボタンを使うと、その前後の行をクリックして表示させることができる。*展開*ボタンを押し続けることによってファイル全体を表示することもできるし、またこの機能はあらゆるGitHubの差分表示ビューに用意されている。

![Expanding Context in Diffs](https://f.cloud.github.com/assets/22635/1610539/863c1f64-5584-11e3-82bf-151b406a272f.gif)

[*差分表示の前後を表示についてもっと詳しく*](https://github.com/blog/1705-expanding-context-in-diffs)

## Emoji

Emojiはプルリクエストやイシュー、READMEなどで`:name_of_emoji:`と書くと利用できる:

```
:smile:
:poop:
:shipit:
:+1:
```

:smile:
:poop:
:shipit:
:+1:

GitHubでサポートされているEmojiの完全なリストは[Emoji cheat sheet for Campfire and GitHub](http://www.emoji-cheat-sheet.com/)か[All-Github-Emoji-Icons](https://github.com/scotch-io/All-Github-Emoji-Icons)で確認できる。

GitHubで使われているEmojiのトップ5は以下の通りだ:

1. :shipit: - `:shipit:`
2. :sparkles: - `:sparkles:`
3. :-1: - `:-1:`
4. :+1: - `:+1:`
5. :clap: - `:clap:`

## 画像及びアニメーションGIF

画像やアニメーションGIFはコミットのコメントやREADMEなどで利用できる:

```
![Alt Text](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)
```

![Peter don't care](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)

あらゆる画像はGitHubでキャッシュされるので、画像のホスティング先が落ちていたとしても変わらず表示されるだろう。

### GitHub Wikiへの画像の添付

GitHub Wikiで画像を追加する方法がいくつかある。通常のMarkdown記法（前節を参照）はもちろん使える。しかしそれだけではなく、画像の幅と高さを指定する記法も使うことができる:

```markdown
[[ http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif | height = 100px ]]
```

こうすると以下のようになる:

![Just a screenshot](http://i.imgur.com/J5bMf7S.png)


## 素早く引用

イシューのスレッドで他の人のコメントを引用してコメントしたい場合、引用したい文章を選択した状態で`r`を押すと、ブロック引用の記法を使ってテキストエリアにコピーされる。

![Quick Quote](http://i.imgur.com/TzpMIOA.png)

[*素早く引用する方法についてもっと詳しく*](https://github.com/blog/1399-quick-quotes)

## Gitステータスのスタイリング

```bash
$ git status
```

![git status](http://i.imgur.com/o3PEHAA.png)

こうすることもできる:

```bash
$ git status -sb
```

![git status -sb](http://i.imgur.com/xNI1bT0.png)

[*Gitの`status`コマンドについてもっと詳しく*](http://git-scm.com/docs/git-status)

## Gitログのスタイリング

```bash
$ git log --all --graph --decorate --oneline --abbrev-commit
```

![git log --all --graph --decorate --oneline --abbrev-commit](http://i.imgur.com/RUPycwI.png)

注: これは[後述の手順](#%E3%82%A8%E3%82%A4%E3%83%AA%E3%82%A2%E3%82%B9)に従ってエイリアスへ追加することもできる。

[*Gitの`log`コマンドについてもっと詳しく*](http://git-scm.com/docs/git-log)

## コミットログの検索

指定した文字列を今までのコミット・メッセージから検索して、もっとも新しいものを表示することができる。

```bash
$ git show :/query
```

`query`を検索したい文字列で置き換えると、最新のコミットがそのコミットにおける差分と同時に表示される。

```bash
$ git show :/typo
```

![git show :/query](http://i.imgur.com/icaGiNt.png)

注: 終了するには`q`を押す。

## マージ済みブランチ

```bash
$ git branch --merged
```

こうすると現在のブランチに既にマージされたブランチの一覧が表示される。

逆にまだマージされていないブランチを表示するには以下のようにする:

```bash
$ git branch --no-merged
```

[*Gitの`branch`コマンドについてもっと詳しく*](http://git-scm.com/docs/git-branch)

## 設定済みライセンスの追加

GitHub上でリポジトリを作成する時、あらかじめ設定されているライセンスを追加することもできる:

![Licese](http://i.imgur.com/Chqj4Fg.png)

既に存在するリポジトリであってもウェブ上のインターフェイスからファイルを作成することで追加できる。`LICENSE`というファイル名にした場合、ライセンスを選択するオプションが表示されるのだ:

![License](http://i.imgur.com/fTjQict.png)

`.gitignore`も同じように作成時に追加することも、後で追加することもできる。

[*オープンソース・ライセンスについてもっと詳しく*](https://help.github.com/articles/open-source-licensing)

## タスクリスト

イシューやプルリクエストでは以下のように（空白に注意）書くとチェックボックスを作成することができる:

```
- [ ] Be awesome
- [ ] Do stuff
- [ ] Sleep
```

![Task List](http://i.imgur.com/k2qZi56.png)

これらチェックボックスにチェックが入れられると、同時にMarkdownソースも更新される:

```
- [x] Be awesome
- [x] Do stuff
- [ ] Sleep
```

[*タスク・リストについてもっと詳しく*](https://github.com/blog/1375%0A-task-lists-in-gfm-issues-pulls-comments)

## 相対リンク

Markdownファイルでリポジトリ内のコンテンツへ張る場合、相対リンクを利用することが推奨されている。

```markdown
[Link to a header](#awesome-section)

[Link to a file](docs/readme)
```

絶対リンクはURLの変更（例: リポジトリのリネーム、ユーザー名の変更、プロジェクトのフォーク）により更新される。  
相対リンクを利用すれば、そのままうまく機能するはずだ。

[*相対リンクについてもっと詳しく*](https://help.github.com/articles/relative-links-in-readmes)

## 推奨したい`.gitconfig`

`.gitconfig`とはあらゆる設定が書き込まれるファイルだ。

### エイリアス

エイリアスはGitの呼び出し方を自分で好きなように定義できるヘルパー機能だ。例えば`git a`で`git add --all`を実行するようにすることができる。

エイリアスを追加するには`~/.gitconfig`を開き、以下のような形式で記述していく:

```
[alias]
	co = checkout
	cm = commit
	p = push
	# Show verbose output about tags, branches or remotes
	tags = tag -l
	branches = branch -a
	remotes = remote -v
```

またはコマンドラインからも設定できる:

```bash
$ git config alias.new_alias git_function
```

例:

```bash
$ git config alias.cm commit
```

注: エイリアスが複数のコマンドからなる場合はクオートで括る必要がある:

```bash
$ git config alias.ac 'add -A . && commit'
```

おすすめの設定を挙げておこう:

| エイリアス | コマンド | 設定方法 |
| --- | --- | --- |
| `git cm` | `git commit` | `git config --global alias.cm commit` |
| `git co` | `git checkout` | `git config --global alias.co checkout` |
| `git ac` | `git add . -A` `git commit` | `git config --global alias.ac '!git add -A && git commit'` |
| `git st` | `git status -sb` | `git config --global alias.st 'status -sb'` |
| `git tags` | `git tag -l` | `git config --global alias.tags 'tag -l'` |
| `git branches` | `git branch -a` | `git config --global alias.branches 'branch -a'` |
| `git remotes` | `git remote -v` | `git config --global alias.remotes 'remote -v'` |

### コマンドの自動修正

多分今は`git comit`とタイプした場合、以下のような出力を得ることだろう:

```bash
$ git comit -m "Message"
# git: 'comit' is not a git command. See 'git --help'.

# Did you mean this?
# 	commit
```

これを`comit`とタイプした時に`commit`を実行させたい場合、自動修正を有効にすれば良い:

```bash
$ git config --global help.autocorrect 1
```

すると以下のような出力を得るようになるだろう:

```bash
$ git comit -m "Message"
# WARNING: You called a Git command named 'comit', which does not exist.
# Continuing under the assumption that you meant 'commit'
# in 0.1 seconds automatically...
```

### 色設定

Gitの出力をカラフルにするには以下のような設定を加えると良い:

```bash
$ git config --global color.ui 1
```

[*Gitの`config`コマンドについてもっと詳しく*](http://git-scm.com/docs/git-config)

# 共有

是非[Twitter](https://twitter.com/intent/tweet?source=webclient&text=http%3A%2F%2Fgithub.com%2Ftiimgreen%2Fgithub-cheat-sheet%20-%20GitHub%20Cheat%20Sheet)でツイートして欲しい。[日本語訳](https://twitter.com/intent/tweet?source=webclient&text=https%3A%2F%2Fgithub.com%2Fhail2u%2Fgithub-cheat-sheet%2Fblob%2Fmaster%2FREADME.ja.md%20-%20GitHub%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0%E3%83%BB%E3%83%9A%E3%83%BC%E3%83%91%E3%83%BC)もよろしく！

# 訳注

これは[GitHub Cheat Sheet](https://github.com/tiimgreen/github-cheat-sheet)の日本語訳である。
