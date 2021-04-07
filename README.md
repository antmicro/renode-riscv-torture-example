# renode-riscv-tortute-example

* To generate .sig files, see: https://github.com/ucb-bar/riscv-torture
* To generate .sig files with Vector instructions, see: https://github.com/Lampro-Mellon/riscv-torture

# tutorial

```
# download renode
mkdir renode
wget https://dl.antmicro.com/projects/renode/builds/renode-latest.linux-portable.tar.gz -O - | tar xz --strip-components=1 -C renode
export PATH="`pwd`/renode:$PATH"

# fix spike test
sed -i 's/\r//g' test.spike.sig

# generate compatible sig file from renode
renode --disable-xwt --console torture.resc | grep "SIG>" | cut -f 2 -d ' ' | sed 's/\r//g' > test.renode.sig

# compare
diff test.renode.sig test.spike.sig
```
