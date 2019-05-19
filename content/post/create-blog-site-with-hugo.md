---
title: "Hugo + Github Pges でブログを作る"
date: 2019-05-19T11:07:47+09:00
archives: "2019"
tags: []
author: Sheeta Sakuramachi
---

## 前提

- Windows10
- gitをインストール済み

<!--001-->
<!--more-->

## Hugoをインストール

Install Hugo[https://gohugo.io/getting-started/installing]

### パッケージマネージャをインストール

Windowsでは[Chocolatey](https://chocolatey.org/)というパッケージマネージャを使ってインストールせよとのことです。

### hugoをインストール
結果
```
PS C:\Windows\system32> choco install hugo -confirm
Chocolatey v0.10.13
Installing the following packages:
hugo
By installing you accept licenses for the packages.
Progress: Downloading hugo 0.55.6... 100%

hugo v0.55.6 [Approved]
hugo package files install completed. Performing other installation steps.
Downloading hugo 64 bit
  from 'https://github.com/gohugoio/hugo/releases/download/v0.55.6/hugo_0.55.6_Windows-64bit.zip'
Progress: 100% - Completed download of C:\Users\lily4\AppData\Local\Temp\chocolatey\hugo\0.55.6\hugo_0.55.6_Windows-64bit.zip (8.09 MB).
Download of hugo_0.55.6_Windows-64bit.zip (8.09 MB) completed.
Hashes match.
Extracting C:\Users\lily4\AppData\Local\Temp\chocolatey\hugo\0.55.6\hugo_0.55.6_Windows-64bit.zip to C:\ProgramData\chocolatey\lib\hugo\tools...
C:\ProgramData\chocolatey\lib\hugo\tools
 ShimGen has successfully created a shim for hugo.exe
 The install of hugo was successful.
  Software installed to 'C:\ProgramData\chocolatey\lib\hugo\tools'

Chocolatey installed 1/1 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).
PS C:\Windows\system32>
```

## ローカルで新しいサイトを作成

## hugoコマンドでサイトを作成

結果
```
PS C:\Users\lily4>
Congratulations! Your new Hugo site is created in C:\Windows\system32\blog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

### テーマを追加

[Hugo Themes](https://themes.gohugo.io/)からテーマを選んで追加します。今回は[Jeffprod](https://themes.gohugo.io/hugo-blog-jeffprod/)を選びました。

```
PS C:\Users\lily4\Documents> cd .\blog\
PS C:\Users\lily4\Documents\blog> git clone https://github.com/Tazeg/hugo-blog-jeffprod.git themes/jeffprod
Cloning into 'themes/jeffprod'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 199 (delta 3), reused 0 (delta 0), pack-reused 188 eceiving objects:  90% (180/199), 556.01 KiB | 1.05 MiB/s
Receiving objects: 100% (199/199), 1.64 MiB | 2.09 MiB/s, done.
Resolving deltas: 100% (92/92), done.
```

```config.toml```を次の内容に変える

```
PS C:\Users\lily4\Documents\blog> code config.toml
```

```
theme = "jeffprod"

[permalinks]
    post = "/:year/:filename"

[taxonomies]
    tag = "tags"
    archive = "archives"
```

### 記事を追加

```
PS C:\Users\lily4\Documents\blog> hugo new post/my-first-post.md
C:\Users\lily4\Documents\blog\content\post\my-first-post.md created
```

<p>
  <img src="@attachment/vscode.png">
</p>

### 表示テスト

```
PS C:\Users\lily4\Documents\blog> hugo server
```