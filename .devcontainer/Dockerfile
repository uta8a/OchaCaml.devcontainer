FROM mcr.microsoft.com/vscode/devcontainers/base:debian

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       ledit \
    && apt-get -y clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspaces/bin
RUN wget http://caml.inria.fr/pub/distrib/caml-light-0.75/cl75unix.tar.gz
RUN wget http://pllab.is.ocha.ac.jp/~asai/OchaCaml/download/OchaCaml.tar.gz
RUN tar xpfvz cl75unix.tar.gz
RUN tar xpfvz OchaCaml.tar.gz
RUN echo '--- OchaCaml/ochacaml	2022-11-24 02:22:24.732635864 +0000\n+++ OchaCaml/patched.ochacaml	2022-11-24 02:23:53.922335619 +0000\n@@ -1,4 +1,4 @@\n #!/bin/sh\n # set srcdir to the src directory of cl75:\n-srcdir=~/cl75/src\n+srcdir=/workspaces/bin/cl75/src\n exec $srcdir/camlrun $srcdir/toplevel/camltop -stdlib $srcdir/lib $*' > exec_cmd.patch
RUN patch -p0 < exec_cmd.patch
RUN sed -i -e 's/-no-cpp-precomp//g' OchaCaml/OchaCaml.diff
RUN patch -p0 < OchaCaml/OchaCaml.diff
WORKDIR /workspaces/bin/cl75/src
RUN make configure
RUN make world
RUN echo 'alias ochacaml="ledit /workspaces/bin/OchaCaml/ochacaml"' >> /home/vscode/.bashrc
RUN . /home/vscode/.bashrc

WORKDIR /workspaces/OchaCaml.devcontainers
