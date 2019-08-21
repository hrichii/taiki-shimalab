---
title: "Pythonソースコードのコメントから仕様書生成"
date: 2019-08-21
draft: false
tags: ["Sphinx", "Python", "docstring"]
---

### **Abstract**
pythonのソースコードにdocstring記法のコメントをすることでsphinxを使って仕様書(.html)を生成する

### **Content**
#### docstringを読み込んで仕様書を生成

```bash
# sphinxのインストール
$ pip install sphinx

# 現在のディレクトリ構成
$ tree /f
C:.
└─src
        main.py
        submodule.py

# sphinxのプロジェクト作成
$ sphinx-quickstart docs
> Separate source and build directories (y/n) [n]:n
> Project name: project_name
> Author name(s): TaikiHoriuchi
> Project release []: 1.0.0
> Project language [en]: ja

# オプションで予め定義できる
#$ sphinx-quickstart docs --author=TaikiHoriuchi -v 1.0.0  -r 1.0.0  --language=ja --no-makefile --no-batchfile --extensions=sphinx.ext.autodoc,sphinx.ext.githubpages,sphinx.ext.napoleon --dot="" --project=project_name

# conf.pyを開く
$ start docs\conf.py

# index.rstを開く
$ start docs\index.rst
```

```python
# conf.pyの中身
import os
import sys
sys.path.insert(0, os.path.abspath('../src/'))

html_theme = 'bizstyle'

extensions = ['sphinx.ext.autodoc' ,'sphinx.ext.githubpages', 'sphinx.ext.napoleon']
# sphinx.ext.autodocは，docstringを自動的に読み込むため.
# sphinx.ext.napoleonはNumpyスタイルかGoogleスタイルのdocstringをパースするため．
```

```
# index.rstの中身
.. toctree::
   :maxdepth: 2
   :caption: Contents:

   main
   submodule
```

```bash
# pythonからrstを生成
$ sphinx-apidoc -f -o ./docs ./src

# rstからhtmlを生成
$ sphinx-build -b singlehtml ./docs ./docs/build

# html確認
$ start docs\_build\index.html

#$ xcopy docs\build %HOMEPATH%\Desktop\taiki@shimalab\docs\post\sphinx\ /E
```

今回作成したhtmlが[こちら](build/index.html)

※ディレクトリに```_```があるとHTMLをリンクできない(何故かよくわかりません)

リポジトリを公開しても良いならGithubPagesを使えば仕様書をgithub上で見せられる．

よきかな

### **References**
- [Qiita sphinxでドキュメント作成からWeb公開までをやってみた](https://qiita.com/kinpira/items/505bccacb2fba89c0ff0)
- [Qiita Sphinxの使い方．docstringを読み込んで仕様書を生成](https://qiita.com/futakuchi0117/items/4d3997c1ca1323259844)
- [Sphinx-Users.jp テーマの変更](https://sphinx-users.jp/cookbook/changetheme/index.html)

### **Source**

- [Github](https://github.com/hrichii/sample_sphinx)【Code】
- [Asgard](<file://///asgard/usr/horiuchi/program/pro_sphinx/repo_sphinx>)【Code】

(Asgardへのアクセスはリンクのアドレスをエクスプローラーに貼付)
