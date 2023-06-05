演習1 個人でのクローン・編集・コミット・プッシュ
=======================================

# 1. リポジトリのフォークとクローン
(1) https://github.com/MasatoshiTada/git-exercises をForkしてください。

(2) ForkしたリポジトリのURL（例： https://github.com/自分のアカウント名/git-exercises ）をコピーしてください（選択肢などはすべてデフォルトのままでOKです）。

(3) ターミナルを起動し、適当なフォルダで次のコマンドを実行してください。リモートリポジトリがローカルにクローンされます。

```bash
$ git clone コピーしたURL
```

(4) 次のコマンドで、git-exercisesフォルダに移動してください。

```bash
$ cd git-exercises
```

# 2. ステージングエリアへの追加
(1) エディタで$ git-exercisesフォルダにあるsample.txtを開いてください。

(2) sample.txtに「おはよう」と記入して保存してください。

(3) 次のコマンドで現在の状態を確認してください。

```bash
$ git status
```

次のように表示されます。これは、sample.txtはまだステージングされていないため、コミット対象外であることを示しています。

```bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   sample.txt
```

> 上記のメッセージにある通り、`git restore sample.txt`とするとファイルの内容が元に戻ります（＝空になる）。

(4) 次のコマンドでsample.txtをステージングしてください。

```bash
$ git add sample.txt
```

(5) 次のコマンドで現在の状態を確認してください。

```bash
$ git status
```

次のように表示されます。これは、sample.txtがステージングされており、コミットの準備が整っていることを示しています。

```bash
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   sample.txt
```

> 上記のメッセージにある通り、`git restore --staged sample.txt`とするとステージングされていない状態に戻ります（ファイルの内容はそのまま）。

# 3. リポジトリへのコミットとプッシュ
(1) 次のコマンドでコミットしてください。

```bash
$ git commit -m "sample.txtに「おはよう」と記入"
```

(2) 次のコマンドで現在の状態を確認してください。

```bash
$ git status
```

次のように表示されます。これは、コミットすべきものが無いことを示しています。

```bash
nothing to commit, working tree clean
```

(3) 次のコマンドでリモートリポジトリにプッシュしてください。

```bash
$ git push origin main
```

(4) ブラウザでGitHubを開き、Forkしたリポジトリにあるsample.txtを開いてください。

sample.txtに「おはよう」と記入されていれば成功です。
