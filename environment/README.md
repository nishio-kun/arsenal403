# CTF環境
DockerでCTFで使う環境を構築します。
よく使うツールをインストール済みのイメージを作成できます。

# 使い方

### build & run:
```shell
docker build -t ctf .
docker run -v "$PWD"/:/usr/ctf -it ctf
```

### system call を使う場合:

```shell
docker run --cap-add=SYS_PTRACE --security-opt="seccomp=unconfined" -v "$PWD"/:/usr/ctf -it ctf
```

# 注意
Docker コンテナ内では system call が制限されているため、例えば、`strace` などのコマンドはデフォルトでは使用できません。
そのため、以下のようなオプションをつけて Docker を起動する必要があります。
ただし、セキュリティレベルが低下するため、使用には注意してください。

Option | Description
--|--
--cap-add | Add Linux capabilities
--security-opt="seccomp=unconfined"	| Turn off seccomp confinement for the container


上記のオプションについての詳細は、以下のドキュメントを参考にしてください。
- https://docs.docker.com/engine/security/seccomp/
- https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities


# ツール

Name | 概要
--|--
[angr](https://angr.io/) | バイナリ解析ツール
[checksec](https://github.com/slimm609/checksec.sh) | 実行ファイルのプロパティをチェック
[gdb](http://sourceware.org/gdb/current/onlinedocs/gdb/) | デバッガ
[gdb-peda](https://github.com/longld/peda) | gdb のプラグイン的なもの
ltrace | デバッグユーティリティ
[one_gadget](https://github.com/david942j/one_gadget) | one-gadget RCE 支援ツール
[pwntools](https://github.com/Gallopsled/pwntools) | CTF用ライブラリ
strace | デバッグユーティリティ
