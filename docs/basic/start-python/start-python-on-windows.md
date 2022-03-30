# Pythonを始める（Windows）

さあ、Pythonをはじめましょう。まずはお手持ちのWindowsでPythonを利用するための環境を構築します。  

## Pythonのバージョン

Pythonのバージョンは大きく分けて2と3があります。それぞれPython 2系やPython 3系と呼ばれます。現在では、Python 2系の開発はストップしており、Python 3系の使用が強く推奨されています。本リポジトリではPython 3系のみを使用します。Python 2系を学ぶ必要はありません。

## <p id="install-python">Pythonのインストール</p>


## <p id="use-interactive-mode">対話モードでPythonを使う</p>

## pyenvのインストール

### pyenvを用いたPythonのインストール

pyenvを用いることで、複数のバージョンのPythonをシステム標準とは独立した環境で導入・管理できます。

ターミナルで次のコマンドを実行し、pyenvを用いてインストールできるPythonのバージョン一覧を確認します。

```shell
> pyenv install --list
```

ここでは、Pythonのバージョン3.8.9と3.9.6をインストールします。

```shell
> pyenv install 3.8.9
> pyenv install 3.9.6
```

pyenvの環境にインストールされているPythonのバージョン一覧を確認します。

```shell
> pyenv versions
* system (set by /Users/user/.pyenv/version)
  3.8.9
  3.9.6
```

ここで、`system` はシステム標準のPythonを、`3.8.9`、`3.9.6` は新しくインストールしたPythonを表しています。`*` は現在使っているPythonを示しています。

Python 3.9.6を使うには、Windows Terminalで次のコマンドを実行します。

```shell
> pyenv global 3.9.6
```

再度、pyenvの環境にインストールされているPythonのバージョン一覧を確認します。

```shell
> pyenv versions
  system
  3.8.9
* 3.9.6 (set by /Users/user/.pyenv/version)
```

Pythonのバージョンを表示して3.9.6であることを確認します。

```shell
> python -V
Python 3.9.6
```

ここで、Pythonの実行コマンドの実体がどこにあるかを確認します。

```shell
> which python
/Users/user/.pyenv/shims/python
```

`~/.pyenv/shims/` にPythonの実体がありました。このディレクトリは、pyenvの仕組みの核となっています。

また、あるディレクトリの中だけで特定のPythonのバージョンを利用することもできます。  
ここでは、次のような `pyenv-demo` というディレクトリの中で作業を行います。

```
pyenv-demo
└── py38
```

ここで、`pyenv-demo/py38` の内部だけでPython 3.8.9を使いたい、といったことがpyenvでは簡単に実現できます。

`pyenv-demo/py38` の内部だけで先ほどインストールしたPython 3.8.9を使うように設定するには、ターミナルで次のコマンドを実行します。

```shell
> cd py38 # py38ディレクトリに移動する
> pyenv local 3.8.9
```

Pythonのバージョンを表示して3.8.9であることを確認します。

```shell
> python -V
Python 3.8.9
```

では、`pyenv-demo` ディレクトリに戻って再度Pythonのバージョンを表示します。

```shell
> cd .. # 親ディレクトリ（pyenv-demo）に移動する
> python -V
Python 3.9.6 
```

`pyenv global` コマンドで設定したPython 3.9.6に戻っています。

## <p id="setup-for-vscode">VS Codeを使った環境構築</p>