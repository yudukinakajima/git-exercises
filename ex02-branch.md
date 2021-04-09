演習2 ローカルリポジトリでのブランチの利用
======================================================

`feature-a` ・ `feature-b` という2つのブランチを作成します。

この演習内のコマンドはすべて、クローンしたgit-exercisesフォルダで実行してください。

# 1. feature-aブランチの作成と作業
(1) 次のコマンドで、現在のブランチが `main` であることを確認してください。

```bash
$ git branch
```

(2) 次のコマンドで、 `feature-a` ブランチを作成・移動してください。

```bash
$ git branch feature-a
$ git switch feature-a
```

> `git switch -c 作成するブランチ名` を利用すると、ブランチの作成・移動が1つのコマンドで行なえます。

(3) 次のコマンドで、現在のブランチが `feature-a` であることを確認してください。

```bash
$ git branch
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

(2) フォルダ内にsample-a.txtが無いことを確認してください。

(3) 次のコマンドで、 `feature-b` ブランチを作成・移動してください。

```bash
$ git branch feature-b
$ git switch feature-b
```

(4) 次のコマンドで、現在のブランチが `feature-b` であることを確認してください。

```bash
$ git branch
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
```

(2) フォルダ内にsample-a.txtがあり、sample-b.txtが無いことを確認してください。

(3) 次のコマンドで、 `main` ブランチに移動してください。

```bash
$ git switch main
```

(4) フォルダ内にsample-a.txt・sample-b.txtが無いことを確認してください。

> 次の演習で使いますので、この演習で作成したブランチはそのままにしておいてください。
