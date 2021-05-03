# Renode RISC-V Torture Example

Copyright (c) 2021 [Antmicro](https://www.antmicro.com)

This repository provides scripts used to test [Renode](https://www.renode.io) RISC-V implementation against the [RISC-V Torture Tests](https://github.com/ucb-bar/riscv-torture).

* To generate ELF and .sig files, see: https://github.com/ucb-bar/riscv-torture
* To generate ELF and .sig files with Vector instructions, see: https://github.com/Lampro-Mellon/riscv-torture

# tutorial
```
# debian:bullseye is recommended but many distros should work.
# download renode
mkdir renode
wget https://dl.antmicro.com/projects/renode/builds/renode-latest.linux-portable.tar.gz -O - | tar xz --strip-components=1 -C renode
export PATH="`pwd`/renode:$PATH"

# generate compatible sig file from renode
renode --disable-xwt --console torture.resc | grep "SIG>" | cut -f 2 -d ' '  > test.renode.sig

# compare
diff -w test.renode.sig test.spike.sig
```
