FROM ubuntu:22.04
ENV PATH=/usr/local/lib/x86_64-linux-musl-cross/bin:/usr/local/lib/aarch64-linux-musl-cross/bin:/usr/local/lib/riscv64-linux-musl-cross/bin:/root/.cargo/bin:$PATH
RUN apt-get update && apt-get upgrade -y && \
    apt-get install wget autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev pkg-config libglib2.0-dev libpixman-1-dev libsdl2-dev git tmux python3 python3-pip ninja-build libclang-dev -y && \
    cd /usr/local/lib && \
    curl https://sh.rustup.rs -sSf > ./rustup && \
    chmod u+x ./rustup && \
    ./rustup --default-toolchain nightly --no-modify-path -y && \
    rustup target add riscv64gc-unknown-none-elf && \
    rustup target add aarch64-unknown-linux-gnu && \
    rustup component add llvm-tools-preview && \
    rustup component add rust-src && \
    cargo install cargo-binutils && \
    wget https://musl.cc/aarch64-linux-musl-cross.tgz && \
    wget https://musl.cc/riscv64-linux-musl-cross.tgz && \
    wget https://musl.cc/x86_64-linux-musl-cross.tgz && \
    tar zxf aarch64-linux-musl-cross.tgz && \
    tar zxf riscv64-linux-musl-cross.tgz && \
    tar zxf x86_64-linux-musl-cross.tgz && \
    wget https://download.qemu.org/qemu-7.0.0.tar.xz && \
    tar xvJf qemu-7.0.0.tar.xz && \
    cd qemu-7.0.0 && \
    ./configure --target-list=riscv64-softmmu,riscv64-linux-user,aarch64-softmmu,aarch64-linux-user && \
    make -j$(nproc) && \
    make install && \
    cd ~ && \
    git clone https://github.com/rcore-os/arceos && \
    cd /root/arceos && \
    make clean && \
    rm /usr/local/lib/*.tgz && \
    rm /usr/local/lib/qemu-7.0.0* -rf && \
    rm /usr/local/lib/rustup && \
    rm ~/.cargo/.crates.toml ~/.cargo/.crates2.json ~/.cargo/.package-cache ~/.cargo/.package-cache-mutate ~/.cargo/registry -rf && \
    apt-get clean
WORKDIR /root/arceos
