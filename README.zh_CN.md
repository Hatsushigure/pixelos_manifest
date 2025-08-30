# PixelOS

[[English](./README.md) | 中文]

## 重要事项

清单文件使用加速链接 (<https://ghfast.top>) 和镜像站 (<https://mirrors.ustc.edu.cn>) 来保证中国大陆用户能够在不使用代理的情况下成功同步. 如果不需要可以直接删除 `https://ghfast.top/` 并将 `https://mirrors.ustc.edu.cn/aosp` 替换为 `https://android.googlesource.com`.

如果 <https://ghfast.top> 不可用, 请将其替换为其他可用的加速链接.

---

## 下载源码

最好先阅读这篇文章了解 [Git 和 Repo](https://source.android.com/docs/setup/download?hl=zh-cn).

用如下命令初始化本地仓库:

```bash
repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs
```

要节省硬盘空间和网络使用 (也更容易同步成功) 可以使用这一条:

```bash
repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen --git-lfs --depth=1
```

_这些命令中的 url 也可以加上加速前缀_

同步仓库:

```bash
repo sync -j4
```

使用中科大镜像时 `-j` 不能超过 4, 不使用时可以随意调整.

## 构建 PixelOS

成功构建需要至少 20GB 内存 (不够可以使用 swap, 越多越好)

使用 `envsetup.sh` 来初始化构建环境:

```bash
source build/envsetup.sh
```

补充完你的设备的所有文件后指定构建目标:

```bash
lunch aosp_devicecodename-aosp_target_release-buildtype
```

开始构建:

```bash
mka bacon -j$(nproc)
```

---

注释:  

**aosp_target_release**: bp1a (As of April ASB)  
**buildtype**: user, userdebug, eng

