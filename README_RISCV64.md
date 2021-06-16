# How to build node/riscv64 using cross compiling build

1. Checkout `v16.X-riscv64` branch
2. Run `./configure`. If using `gcc`, we have to use `-Wno-narrowing`. Also if you want to turn on OpenSSL, we have to set `--shared-openssl` since we don't have right build configuration file to build OpenSSL in tree.
```sh
CC=riscv64-linux-gnu-gcc CXX="riscv64-linux-gnu-g++ -Wno-narrowing" \
  CC_host=gcc CXX_host="g++ -Wno-narrowing" \
  ./configure --prefix=../install --dest-cpu=riscv64 --dest-os=linux --cross-compiling --shared-zlib --shared-openssl
```
3. Run `make`
```sh
make -j16
```

# Notes
* `--ninja` won't work on cross build.
