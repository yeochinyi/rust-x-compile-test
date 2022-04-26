https://github.com/KodrAus/rust-cross-compile

add this to .cargo/config.toml

# For Windows (dont work for modules with native compilation i.e openssl)

[target.x86_64-pc-windows-msvc]
rustflags = ["-C", "target-feature=+crt-static"]

[target.x86_64-unknown-linux-musl]
linker = "rust-lld"

# https://releases.linaro.org/components/toolchain/binaries/

[target.aarch64-unknown-linux-gnu]

# linker = "C:/app/gcc/gcc-linaro-5.5.0-2017.10-i686-mingw32_aarch64-linux-gnu/bin/aarch64-linux-gnu-gcc-5.5.0.exe"

linker = "C:\\app\\gcc\\gcc-linaro-7.5.0-2019.12-i686-mingw32_aarch64-linux-gnu\\bin\\aarch64-linux-gnu-gcc-7.5.0.exe"

[target.armv7-unknown-linux-gnueabihf]
linker = "C:\\app\\gcc\\gcc-linaro-7.5.0-2019.12-i686-mingw32_arm-linux-gnueabihf\\bin\\arm-linux-gnueabihf-gcc.exe"

# For WSL (OK for native modules)

but have to use vendored i.e. openssl-sys = { version = "0.9.72", features = ["vendored"] }

https://howtoinstall.co/en/gcc-aarch64-linux-gnu
sudo apt install aarch64-linux-gnu-gcc

[target.aarch64-unknown-linux-gnu]
linker = "aarch64-linux-gnu-gcc"
