演習5 GitHubでのプルリクエストとコンフリクトの解消
========================================================

コンフリクトは、GitHubでブランチをマージする際にも起こりえます。それをGitHub上で解決します。

今回の演習では、「他の人」「マージ担当」の作業も自分で行います（1人3役）。

この演習が成功した後、sample.txtは次のようになっています。

```
おはよう
おやすみなさい
再びおはよう
```

この演習内のコマンドはすべて、クローンしたgit-exercisesフォルダで実行してください。

# 1. 他の人（実は自分）の作業
(1) https://github.com/自分のアカウント名/git-exercises にアクセスしてください。

(2) ブラウザでsample.txtを開いた後、画面右上にある[Edit this file]ボタン（ペンのアイコン）をクリックしてください。

(3) 最後の行に「再びおはよう」を追記してください。

作業完了後のsample.txtは次のようになっています。

```
おはよう
再びおはよう
```

(4) [Commit changes...]をクリック後、[Commit message]に「sample.txtに「再びおはよう」を追加」と記入して、[Commit changes]をクリックしてください。

# 2. 自分の作業 - ブランチの作成
(1) 次のコマンドでローカルリポジトリにブランチを作成してください。

```bash
$ git switch -c add-gn
Switched to a new branch 'add-gn'
```

(2) 次のコマンドで現在のブランチが `add-gn` であることを確認してください。

```bash
$ git branch
* add-gn
  main
```

(3) エディタでsample.txtを開いた後、最後の行に「おやすみなさい」を追記・保存してください。

作業完了後のsample.txtは次のようになっています。

```
おはよう
おやすみなさい
```

(4) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample.txt
$ git commit -m "sample.txtに「おやすみなさい」を追加"
[add-gn 6194a12] sample.txtに「おやすみなさい」を追加
 1 file changed, 2 insertions(+), 1 deletion(-)
```

(5) 次のコマンドでプッシュおよびリモートブランチの作成を行ってください。

```bash
$ git push origin add-gn
Enumerating objects: 49, done.
Counting objects: 100% (49/49), done.
Delta compression using up to 8 threads
Compressing objects: 100% (29/29), done.
Writing objects: 100% (49/49), 12.81 KiB | 1.83 MiB/s, done.
Total 49 (delta 20), reused 25 (delta 10), pack-reused 0
remote: Resolving deltas: 100% (20/20), done.
remote: 
remote: Create a pull request for 'add-gn' on GitHub by visiting:
remote:      https://github.com/xxxxxx/git-exercises/pull/new/add-gn
remote: 
To https://github.com/xxxxxx/git-exercises
 * [new branch]      add-gn -> add-gn
```

(6) 次のコマンドで、まだ現在のブランチが `add-gn` であることを確認してください。

```bash
$ git branch
* add-gn
  main
```

# 3. 自分の作業 - プルリクエストの作成
(1) ブラウザで https://github.com/自分のアカウント名/git-exercises にアクセスしてください。

(2) 画面上側のメニューにある[Pull requests]をクリックしてください。

> 画面上側に[Compare & pull request]という緑色のボタンがある場合は、これをクリックしてください。この場合は(3)と(4)の手順は飛ばされます。

(3) [New pull request]をクリックしてください。

(4) [base repository]で「自分のアカウント名/git-exercises」、「[base]で「main」、[compare]で「add-gn」を選択すると、[Can’t automatically merge.]と表示されます。これは、競合が起きていることを示します。この状態でもプルリクエストを作成することは可能ですので、[Create pull request]をクリックしてください。

(5) [Open a pull request]画面で、各項目に次のように記入してください。

- [Title]に「「おやすみなさい」機能の追加」
- [Leave a comment]に「sample.txtに「おやすみなさい」を追加」

記入できたら[Create pull request]をクリックしてください。

# 4. マージ担当（実は自分）の作業 - コンフリクトの解消とマージ
(1) ブラウザで表示されたプルリクエスト[「おやすみなさい」機能の追加]の画面で、[Resolve conflicts]をクリックしてください。

(2) sample.txtをブラウザ上で編集できるようになりますので、次のように編集してください。

```
おはよう
おやすみなさい
再びおはよう
```

(3) [Mark as resolved]をクリック→[Commit merge]をクリックしてください。これにより `add-gn` ブランチのsample.txtが、編集した内容に変更されます。

(4) [Merge pull request]をクリック→[Confirm merge]をクリックしてください。これで `main` ブランチへマージが完了しました。

(5) 少し待って画面上部に[Merged]と表示された後、[Delete branch]をクリックしてください。これによりリモートリポジトリから `add-gn` ブランチが削除されます。

# 5. 自分の作業 - ローカルリポジトリへの反映
(1) 次のコマンドで `main` ブランチに移動してください。

```bash
$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

(2) 次のコマンドで現在のブランチが `main` であることを確認してください。

```bash
$ git branch
```

(3) 次のコマンドで、リモートリポジトリの `main` ブランチの最新状態を、ローカルリポジトリの `main` ブランチに反映してください。

```bash
$ git fetch
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 7 (delta 2), reused 1 (delta 0), pack-reused 0
Unpacking objects: 100% (7/7), 2.07 KiB | 162.00 KiB/s, done.
From https://github.com/MasatoshiTada8888/git-exercises
   d0a1f5c..11f227c  main       -> origin/main
$ git merge origin/main
Updating d0a1f5c..11f227c
Fast-forward
 sample.txt | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
```

(4) エディタでsample.txtの内容を確認してください。次のようになっているはずです。

```
おはよう
おやすみなさい
再びおはよう
```

(5) 次のコマンドで、ローカルリポジトリの `add-gn` ブランチを削除してください。

```bash
$ git branch -D add-gn
```

(6) 次のコマンドで、ブランチが `main` のみになっていることを確認してください。

```bash
$ git branch
* main
```
