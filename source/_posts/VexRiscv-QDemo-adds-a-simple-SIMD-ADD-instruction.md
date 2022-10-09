---
title: VexRiscv Demo - adds a simple SIMD_ADD instruction
date: 2022-10-09 21:35:16
tags:
---
## Dependencies:
```bash
$ sudo apt-get update
$ sudo apt install git make autoconf g++ flex bison openjdk-8-jdk automake autotools-dev curl python3 libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev gtkwave -y
$ echo "deb https://repo.scala-sbt.org/scalasbt/debian all main" | sudo tee /etc/apt/sources.list.d/sbt.list
$ echo "deb https://repo.scala-sbt.org/scalasbt/debian /" | sudo tee /etc/apt/sources.list.d/sbt_old.list
$ curl -sL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x2EE0EA64E40A89B84B2DF73499E82A75642AC823" | sudo apt-key add
$ sudo apt-get update
$ sudo apt-get install sbt
```
## Verilator:
```bash
$ git clone http://git.veripool.org/git/verilator
$ cd verilator
$ git checkout v4.216
$ autoconf
$ ./configure
$ make
$ sudo make install
```
## Vexriscv
```bash
$ git clone https://github.com/SpinalHDL/VexRiscv.git
$ cd VexRiscv
$ sbt "runMain vexriscv.demo.GenCustomSimdAdd"
$ cd src/test/cpp/regression/
$ make clean run IBUS=SIMPLE DBUS=SIMPLE CSR=no MMU=no DEBUG_PLUGIN=no MUL=no DIV=no DHRYSTONE=no REDO=2 CUSTOM_SIMD_ADD=yes TRACE=yes
$ gtkwave custom_simd_add.fst
```