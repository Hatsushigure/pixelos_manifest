# PixelOS

[English | [中文](./README.zh_CN.md)]

## NOTICE

The manifests use accelerator (<https://ghfast.top>) and mirror (<https://mirrors.ustc.edu.cn>) to ensure Chinese users can successfully sync without VPN. If you don't need them, you can simply delete prefix `https://ghfast.top/` and replace `https://mirrors.ustc.edu.cn/aosp` with `https://android.googlesource.com`.

If the <https://ghfast.top> accelerator fails, replace it with other available github accelerators.

---

## Getting Started

To get started with the PixelOS sources, you'll need to get
familiar with [Git and Repo](https://source.android.com/setup/build/downloading).

To initialize your local repository, use command:

```bash
repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs
```

or if you have a poor internet connection or small disk, use this:

```bash
repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs --depth=1
```

_Adding an accelerator prefix to the url is also OK._

Then sync up:

```bash
repo sync -j4
```

If you use the ustc mirror, -j value cannot be greater than 4, otherwise you can use any value you like.

## Building the System

To successfully build the system, you need more than 20GB RAM (you can use swap if not enough, more is better).

Initialize the ROM environment with the `envsetup.sh` script.

```bash
source build/envsetup.sh
```

Lunch your device after cloning all device sources if needed.

```bash
lunch aosp_devicecodename-aosp_target_release-buildtype
```

Start compilation

```bash
mka bacon -j$(nproc)
```

---

Note:  

**aosp_target_release**: bp1a (As of April ASB)  
**buildtype**: user, userdebug, eng

