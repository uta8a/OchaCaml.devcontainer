# OchaCaml.devcontainer

[OchaCaml: shift/reset-extension of Caml Light](http://pllab.is.ocha.ac.jp/~asai/OchaCaml/) をdevcontainerで使いやすくします。

# Usage

- Open in Containerをします
- ビルドするのでちょっと待つ
- `ochacaml` と打つと立ち上がる

```sh
$ ochacaml
>       Caml Light version 0.75 + shift/reset

# 
```

# Changes

- `-no-cpp-precomp` でmake時にエラーを吐くので修正
- `ochacaml` コマンドで本体を見にいく時、ビルドした成果物が置いてある `/workspaces/bin/cl75/src` をみるよう変更
- `ledit` を導入してコマンドラインでの編集を可能にした
