# QvMeta

Meta repository for building Qv2ray statically.

```bash
git clone https://github.com/Shadowsocks-NET/QvMeta.git
cd QvMeta
git clone --recursive https://github.com/Shadowsocks-NET/Qv2ray.git
git clone --recursive https://github.com/Shadowsocks-NET/QvPlugins.git
cd ..
mkdir QvMeta-build && cd QvMeta-build
cmake ../QvMeta \
    -DBUILD_TESTING=OFF \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=installed \
    -DQV2RAY_BUILD_INFO="Qv2ray Static Nightly Build for AUR" \
    -DQV2RAY_DEFAULT_VASSETS_PATH="/usr/share/v2ray" \
    -DQV2RAY_DEFAULT_VCORE_PATH="/usr/bin/v2ray" \
    -DQV2RAY_AUTO_UPDATE=OFF \
    -DUSE_SYSTEM_LIBUV=OFF \
    -DUSE_SYSTEM_UVW=OFF \
    -GNinja
cmake --build . --parallel
cmake --install .
```
