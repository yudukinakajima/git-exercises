演習2 ローカルリポジトリでのブランチの利用
======================================================

`feature-a` ・ `feature-b` という2つのブランチを作成します。

この演習内のコマンドはすべて、クローンしたgit-exercisesフォルダで実行してください。

# 1. feature-aブランチの作成と作業
(1) 次のコマンドで、現在のブランチが `main` であることを確認してください。

```bash
$ git branch
* main
```

> ブランチが複数ある場合は、ブランチ名が複数列挙されます。その中で`*`が付いているのが、現在のブランチです。

(2) 次のコマンドで、 `feature-a` ブランチを作成・移動してください。

```bash
$ git switch -c feature-a
Switched to a new branch 'feature-a'
```

(3) 次のコマンドで、現在のブランチが `feature-a` であることを確認してください。

```bash
$ git branch
* feature-a
  main
```

(4) フォルダ内にsample-a.txtを新規作成し、「Aから追加」と記入・保存してください。

(5) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample-a.txt
$ git commit -m "sample-a.txtを作成"
```

# 2. feature-bブランチの作成と作業
(1) 次のコマンドで、 `main` ブランチに移動してください。

```bash
$ git switch main
```

> `git switch`コマンドで`-c`オプションを付けなかった場合は、ブランチを移動するだけになります（ブランチの新規作成は行われません）。

(2) フォルダ内にsample-a.txtが無いことを確認してください。

(3) 次のコマンドで、 `feature-b` ブランチを作成・移動してください。

```bash
$ git switch -c feature-b
Switched to a new branch 'feature-b'
```

(4) 次のコマンドで、現在のブランチが `feature-b` であることを確認してください。

```bash
$ git branch
  feature-a
* feature-b
  main
```

(5) フォルダ内にsample-b.txtを新規作成し、「Bから追加」と記入・保存してください。

(6) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample-b.txt
$ git commit -m "sample-b.txtを作成"
```

# 3. 確認
(1) 次のコマンドで、 `feature-a` ブランチに移動してください。

```bash
$ git switch feature-a
Switched to branch 'feature-a'
```

(2) フォルダ内にsample-a.txtがあり、sample-b.txtが無いことを確認してください。

(3) 次のコマンドで、 `main` ブランチに移動してください。

```bash
$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

(4) フォルダ内にsample-a.txt・sample-b.txtが無いことを確認してください。

> 次の演習で使いますので、この演習で作成したブランチはそのままにしておいてください。
