演習4 ローカルリポジトリでの競合の解消
======================================================

`feature-a` ブランチで機能追加を行い、それを `main` にマージします。その時に発生する競合を解消します。

この演習内のコマンドはすべて、クローンしたgit-exercisesフォルダで実行してください。

# 1. feature-aブランチでの機能追加
(1) 次のコマンドで、 `feature-a` ブランチに移動してください。

```bash
$ git switch feature-a
Switched to branch 'feature-a'
```

(2) 次のコマンドで、現在のブランチが `feature-a` であることを確認してください。

```bash
$ git branch
* feature-a
  feature-b
  main
```

(3) フォルダ内にsample-a.txtがあり、sample-b.txtが無いことを確認してください。

(4) sample-a.txtの最終行に、「Aから追加2」と記入・保存してください。

sample-a.txtの内容は次のようになります。

```
Aから追加
Aから追加2
```

(5) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample-a.txt
$ git commit -m "sample-a.txtに追記"
```

# 2. feature-aをmainにマージ→競合発生
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

(3) フォルダ内にsample-a.txt・sample-b.txtが共にあることを確認してください。

(4) sample-a.txtを開き、次のようになっていることを確認してください。

```
Aから追加
Bから追加
```

(5) 次のコマンドで、 `feature-a` ブランチを `main` ブランチにマージしてください。

```bash
$ git merge feature-a
```

すると、競合があるためマージに失敗した旨が表示されます。

```bash
Auto-merging sample-a.txt
CONFLICT (content): Merge conflict in sample-a.txt
Automatic merge failed; fix conflicts and then commit the result.
```

> mainブランチのsample-a.txtの2行目には「Bから追加」（feature-bで追記しmainにマージしたもの）が書かれています。対してfeature-aブランチのsample-a.txtの2行目には「Aから追加2」が書かれています。これにより競合が発生しています。

# 3. 競合の解消とコミット

(1) エディタでsample-a.txtを開いてください。内容は次のようになっています。

```
Aから追加
<<<<<<< HEAD
Bから追加
=======
Aから追加2
>>>>>>> feature-a
```

これをエディタで次のように修正してください。修正後は保存してエディタを閉じてください。

```
Aから追加
Bから追加
Aから追加2
```

(2) 次のコマンドでステージングとコミットを行ってください。

```bash
$ git add sample-a.txt
$ git commit -m "feature-aをmainにマージ"
[main d0a1f5c] feature-aをmainにマージ
```

(3) 次のコマンドでリモートリポジトリにプッシュしてください。

```bash
$ git push origin main
Enumerating objects: 18, done.
Counting objects: 100% (18/18), done.
Delta compression using up to 8 threads
Compressing objects: 100% (12/12), done.
Writing objects: 100% (17/17), 1.44 KiB | 368.00 KiB/s, done.
Total 17 (delta 8), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (8/8), completed with 1 local object.
To https://github.com/xxxxxx/git-exercises
   85d4fd9..d0a1f5c  main -> main
```

(4) ブラウザで、Forkしたプロジェクトを開いてください。sample-a.txtとsample-b.txtがあれば成功です。

# 4. 後片付け
(1) 次のコマンドで `feature-a` ブランチを削除してください。

```bash
$ git branch -D feature-a
Deleted branch feature-a (was 462b280).
```

(2) 次のコマンドで `feature-b` ブランチを削除してください。

```bash
$ git branch -D feature-b
Deleted branch feature-b (was 06fb7e8).
```

(3) 次のコマンドでブランチが `main` のみになっていることを確認してください。

```bash
$ git branch
* main
```
