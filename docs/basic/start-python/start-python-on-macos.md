# Mac OSでPythonを始める

さあ、Pythonをはじめましょう。まずはお手持ちのMacでPythonを利用するための環境を構築します。  

## Pythonのバージョン

Pythonのバージョンは大きく分けて2と3があります。それぞれPython 2系やPython 3系と呼ばれます。現在では、Python 2系の開発はストップしており、Python 3系の使用が強く推奨されています。本リポジトリではPython 3系のみを使用します。Python 2系を学ぶ必要はありません。

## Pythonのインストール

ここでは、Pythonをシステムにインストールします。  
Mac OSの場合、あらかじめシステムにPythonがインストールされていることがほとんどです。しかし、多くの場合はバージョンが古いので、新しいバージョンのPythonをインストールします。

Pythonのインストールには、pyenvというツールを使います。  
pyenvを用いることで、複数のバージョンのPythonをシステム標準とは独立した環境で導入・管理できます。  
Mac OSにpyenvをインストールするには、[Mac OSにpyenvをインストールする](/docs/appendix/how-to-install-pyenv-on-macos.md)を参照してください。

pyenvのインストールが完了したら、ターミナルで次のコマンドを実行し、pyenvを用いてインストールできるPythonのバージョン一覧を確認します。

```shell
> pyenv install --list
```

ここでは、Pythonのバージョン3.9.6をインストールします。

```shell
> pyenv install 3.9.6
```

pyenvの環境にインストールされているPythonのバージョン一覧を確認します。

```shell
> pyenv versions
* system (set by /Users/user/.pyenv/version)
  3.9.6
```

ここで、`system` はシステム標準のPythonを、`3.9.6` は新しくインストールしたPythonを表しています。`*` は現在使っているPythonを示しています。

デフォルトでPython 3.9.6を使うようにするには、ターミナルで次のコマンドを実行します。

```shell
> pyenv global 3.9.6
```

再度、pyenvの環境にインストールされているPythonのバージョン一覧を確認します。

```shell
> pyenv versions
  system
* 3.9.6 (set by /Users/***/.pyenv/version)
```

現在使っているPythonのバージョンは3.9.6であることがわかりました。  
また、次のコマンドでも、現在使っているPythonのバージョンを確認できます。

```shell
> python -V
Python 3.9.6
```

これでPythonのインストールは完了です。

## 対話モードでPythonを使う

Pythonを対話モードで実行します。  
ターミナルで次のコマンドを実行します。

```shell
> python
```

このコマンドはPythonの対話モードに入るようにシステムに命令します。  
実行すると、

```python
Python 3.9.6 (default, Mar 12 2022, 08:45:35)
[Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

などと表示され、文字が入力できる状態になったかと思います。この対話モードでは、Pythonコードを対話的に実行できます。

試しにこの対話モードで「Hello World！」の文字列を表示してみます。

```python
>>> print("Hello World!")
Hello World!
```

また、簡単な演算をしてみます。

```python
>>> x = 123 + 234
>>> print(x)
357
```

対話モードを終了するには、`Ctrl` + `D` を押すか、対話モード上で `exit()` と打ち込みます。

ここでご紹介したものは、Pythonの機能のほんの一部です。
後のセクションではPythonのさまざまな機能を学んでいきます。
楽しみにしていてください。

## Visual Studio Codeを使った環境構築

[Visual Studio Code](https://code.visualstudio.com/) (VS Code) は、コーディングのための便利なエディタです。  
Pythonのための便利で豊富な拡張機能を簡単に利用でき、Pythonのコーディングを効率良く行うことができます。  
Mac OSにVS Codeをインストールするには、[Mac OSにVisual Studio Codeをインストールする](/docs/appendix/how-to-install-vscode-on-macos.md)を参照してください。

--- 

### :tada: 本セクションは終了です。次のセクションに進んでください。

**[> データ型を理解する](/docs/basic/data-types.md)**