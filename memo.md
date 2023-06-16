# git 


## git add

指定したファイルをインデックスに登録してコミット対象とするコマンド
インデックスとはワークツリーとリポジトリの間にあるコミット準備を行う場所（日本語だと追跡対象ファイル等ということが多い）

https://backlog.com/ja/git-tutorial/intro/04/

## git addのオプション

### `-u`

> Update the index just where it already has an entry matching pathspec. This removes as well as modifies index entries to match the working tree, but adds no new files.
If no pathspec is given when -u option is used, all tracked files in the entire working tree are updated (old versions of Git used to limit the update to the current directory and its subdirectories).

`git add hoge`の`hoge`にあたるのがpathspec.

更新，削除された追跡対象ファイルが追加される。新規追加されたファイルは対象にならない。なので新しいファイルを作ってその後`git add -u .`をしても新しく作ったファイルは`Untracked`の状態のままとなる。

https://ama-tech.hatenablog.com/difference-between-git-add-a-and-u

### -A

> add changes from all tracked and untracked files

削除変更追加されたもの全部を追跡対象に追加する

## git rm

基本はrmコマンドと同じだが，その変更をgitに反映させることができるのでファイルを削除したことをわざわざ`add`コマンドで追跡対象を確認する必要がない。

### -r

`recursive` 再帰的に行う。ディレクトリ内のファイルすべてに対して処理を行うときなどに付ける。

### git config

gitに関する情報を設定したり閲覧したりするコマンド。名前とメアドなどを変えることができるが，逆に言えば何の対策もしてなければなりすますこともできる。それの対策として，PGP署名付きコミットがある。ちなみにPGPとは`Pretty Good Privacy`らしい。

#### PGP GPGの違い

まず，`PGP`は公開鍵暗号方式を用いた暗号署名ができる仕組みのこと。PGPの仕様はRFC(RFC4880)に公開されて現在は`OpenPGP`という名前で標準化されている。 これに準拠した実装として`GPG(Gnu Privacy Good)`がある。
つまり，`PGP`はプロトコルで，`GPG`はプログラムの名前というだけ。

## git commit

> Create a new commit containing the current contents of the index and the given log message describing the changes. The new commit is a direct child of HEAD, usually the tip of the current branch, and the branch is updated to point to it (unless no branch is associated with the working tree, in which case HEAD is "detached" as described in git-checkout(1)).

要するに，追跡対象の現在の内容と新しい変更点のログメッセージを含むコミットを作るコマンド。ここで作られる新しいコミットはHEADコミットの子の部分につくられ，基本的には現在のブランチの最先端に作られる。

だいたいは`git commit -am "commit message"`という感じになる。
