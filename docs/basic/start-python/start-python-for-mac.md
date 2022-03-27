# Pythonを始める（Mac）

さあ、Pythonをはじめましょう。まずはお手持ちのMacでPythonを利用するための環境を構築します。  

## Pythonのバージョン

Pythonのバージョンは大きく分けて2と3があります。それぞれPython 2系やPython 3系と呼ばれます。現在では、Python 2系の開発はストップしており、Python 3系の使用が強く推奨されています。本リポジトリではPython 3系のみを使用します。Python 2系を学ぶ必要はありません。

## <p id="install-python">Pythonのインストール</p>

ここでは、Pythonをシステムにインストールします。  
Macの場合、あらかじめシステムにPythonがインストールされていることがほとんどです。  
ターミナルで次のコマンドを実行してインストールされているPythonのバージョンを確認します。 `-V` オプションはバージョンを表示するという意味です。

```shell
> python -V
```
- **`Python 2.*.*`（`*` は任意の数字）と表示された場合**  
  Python 2系がシステムの標準となっています。Python 3系を利用できるように設定する必要があります。

- **`Python 3.*.*` と表示された場合**  
  Python 3系がシステムのデフォルトとなっています。本チャプターは読み飛ばしていただいて構いません。

- **`zsh: python: command not found` などと表示された場合**  
  システムにPythonがインストールされていないか、何らかのトラブルでPythonが利用できていない状態です。[トラブルシューティング](trouble-shooting.md)を参照してください。

また、次のコマンドを実行してインストールされているpython 3系のバージョンを確認します。

```shell
> python3 -V
```
- **`Python 3.*.*` と表示された場合**  
  Python 3系がシステムにインストールされています。[エイリアスを作成する](#alias-python-is-python3)に進んでください。

- **`zsh: python3: command not found` などと表示された場合**  
  システムにPython 3系がインストールされていないか、何らかのトラブルでPython 3系が利用できていない状態です。[トラブルシューティング](trouble-shooting.md)を参照してください。

### <p id="alias-python-is-python3">エイリアスを作成する</p>

ターミナルで次のコマンドを実行してください。

```sh
> alias python=python3
```

再度Pythonのバージョンを確認すると、今度は `Python 3.*.*` と表示されたかと思います。  
これは一時的にエイリアスを用いて `python` というコマンドを `python3` と読み替えて実行するようにシステムに命令したためです。  
このエイリアスはPCを再起動するたびにリセットされるため、永続化したい場合にはログインシェルを書き換える必要があります。（ここでは永続化させる必要はありません！）

## <p id="use-interactive-mode">対話モードでPythonを使う</p>

Pythonを対話モードで実行します。  
ターミナルで次のコマンドを実行します。
```shell
> python
```
このコマンドはPythonの対話モードに入るようにシステムに命令します。  
実行すると、
```python
Python 3.8.9 (default, Oct 26 2021, 07:25:54)
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
対話モードを終了するには、`Ctrl` + `D` を押すか、対話モード上で`exit()`と打ち込みます。

ここでは、実行したPythonコードの意味について理解する必要はありません。後のセクションで具体的に解説します。

## pyenvのインストール

システムに標準でインストールされているPythonを実業務で使うのはあまり好ましくありません。これは、誤って標準のPython環境を破壊してしまった場合、システムの一部がうまく動作しないことにつながる可能性があるからです。

ここでは、pyenvというパッケージを使って、システム標準とは独立した環境でPythonを使えるようにします。

ターミナルで次のコマンドを実行してpyenvがインストールされているかを確認します。

```shell
> pyenv -v
```

- **`pyenv 2.*.*` などと表示された場合**  
   pyenvがすでにインストールされています。本チャプターは読み飛ばしていただいて構いません。

### Homebrewのインストール

Homebrewは、Mac OS上でパッケージの導入・管理を簡単に行えるようにするためのツールです。  
Homebrewに登録されているパッケージは、単純なコマンドを実行するだけでインターネットからインストールできます。

ターミナルで次のコマンドを実行してHomebrewがインストールされているかを確認します。

```shell
> brew -v
```

- **`zsh: command not found: brew` などと表示された場合**
   [Homebrew公式サイト](https://brew.sh/index_ja)を参照してシステムにHomebrewをインストールしてください。

- **`Homebrew 3.*.* ...` などと表示された場合**  
   Homebrewがすでにインストールされています。

### Homebrewを用いたpyenvのインストール

Homebrewを用いてpyenvをインストールします。  
ターミナルで次のコマンドを実行します。

```shell
> brew update # Homebrewをアップデートする
> brew install pyenv # Homebrewを用いてpyenvをインストールする
```

実行が正常に完了したら、ターミナルで次のコマンドを実行し、ログインシェルにpyenv用の設定項目を追記し、反映します。

```shell
> echo '# Setting for pyenv' >> ~/.zshrc
> echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
> echo 'eval "$(pyenv init -)"' >> ~/.zshrc
> source ~/.zshrc
```

ターミナルで次のコマンドを実行し、pyenvがインストールされていることを確認します。

```shell
> pyenv -v
```

pyenvのインストールに関してトラブルが生じた場合は、[pyenvのGithubリポジトリ](https://github.com/pyenv/pyenv)を参照してください。

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

Python 3.9.6を使うには、ターミナルで次のコマンドを実行します。

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