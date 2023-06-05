演習3 ローカルリポジトリでのブランチのマージ
======================================================

演習2で作成した `feature-a` ・ `feature-b` ブランチを `main` にマージします。

この演習内のコマンドはすべて、クローンしたgit-exercisesフォルダで実行してください。

# 1. feature-aをmainにマージ
(1) 次のコマンドで、 `main` ブランチに移動してください。

```bash
$ git switch main
```

(2) 次のコマンドで、現在のブランチが `main` であることを確認してください。

```bash
$ git branch
  feature-a
  feature-b
* main
```

(3) フォルダ内にsample-a.txt・sample-b.txtが共に無いことを確認してください。

(4) 次のコマンドで、 `feature-a` ブランチを `main` ブランチにマージしてください。

```bash
$ git merge feature-a
Updating 85d4fd9..e3d2163
Fast-forward
 sample-a.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 sample-a.txt
```

(5) フォルダ内にsample-a.txtがあり、「Aから追加」と書かれていることを確認してください。

# 2. feature-bにmainの最新状態をマージしてから機能を追加
(1) 次のコマンドで、 `feature-b` ブランチに移動してください。

```bash
$ git switch feature-b
```

(2) 次のコマンドで、現在のブランチが `feature-b` であることを確認してください。

```bash
$ git branch
  feature-a
* feature-b
  main
```

(3) フォルダ内にsample-a.txtが無く、sample-b.txtがあることを確認してください。

(4) 次のコマンドで、 `main` ブランチを `feature-b` ブランチにマージしてください。

```bash
$ git merge main
```

(5) フォルダ内にsample-a.txt・sample-b.txtが共にあることを確認してください。

(6) sample-a.txtの最終行に、「Bから追加」と記入・保存してください。

(7) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample-a.txt
$ git commit -m "sample-a.txtに追記"
[feature-b 06fb7e8] sample-a.txtに追記
 1 file changed, 2 insertions(+), 1 deletion(-)
```

# 3. 機能追加後のfeature-bをmainにマージ
(1) 次のコマンドで、 `main` ブランチに移動してください。

```bash
$ git switch main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
```

(2) 次のコマンドで、現在のブランチが `main` であることを確認してください。

```bash
$ git branch
  feature-a
  feature-b
* main
```

(3) フォルダ内にsample-a.txtがあり、sample-b.txtが無いことを確認してください。

(4) sample-a.txtを開き、「Aから追加」のみが書かれていることを確認してください。確認後はファイルを閉じてください。

(5) 次のコマンドで、 `feature-b` ブランチを `main` ブランチにマージしてください。

```bash
$ git merge feature-b
Updating e3d2163..06fb7e8
Fast-forward
 sample-a.txt | 3 ++-
 sample-b.txt | 1 +
 2 files changed, 3 insertions(+), 1 deletion(-)
 create mode 100644 sample-b.txt
```

(6) フォルダ内にsample-a.txt・sample-b.txtが共にあることを確認してください。

(7) sample-a.txtを開き、「Aから追加」「Bから追加」の両方が書かれていることを確認してください。

(8) 次のコマンドで、3つのブランチ `main` ・ `feature-a` ・ `feature-b` がまだ存在することを確認してください。

```bash
$ git branch
  feature-a
  feature-b
* main
```

> 次の演習で使いますので、各ブランチは削除しないでください。
