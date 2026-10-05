# RickyOS 默认待机图片

RickyOS（MindReset Read Pico 固件）在「待机显示」和「设置 → 电源与待机」里提供「下载默认图片」，从这里下载。

| 文件 | 设备上的名字 |
| --- | --- |
| `wallpapers/01-mountains.bmp` | 云海 |
| `wallpapers/02-window.bmp` | 窗边 |
| `wallpapers/03-cat.bmp` | 猫与书 |
| `wallpapers/04-moon.bmp` | 月夜 |
| `wallpapers/05-bamboo.bmp` | 竹 |
| `wallpapers/06-lamp.bmp` | 夜灯 |

- `wallpapers/*.bmp`：684×1216，4 位 16 级灰阶调色板，对应 Read Pico 的 16 级灰度屏，设为壁纸时原样复制，不再转换。
- `wallpapers.json`：下载清单，文件地址指向 GitHub Release。
- `mirror.json`：同一份清单，文件地址经 jsDelivr 镜像本仓库的 `wallpapers/`。
- 两份清单的 `mirrors` 列出其他存放相同文件的地址，某个文件下载失败时设备会依次换用。
- `sources/`：原图（1024×1536）。`build_rickyos_wallpapers.py` 把原图居中裁成 9:16、缩放并抖动到 16 级灰阶，生成上面的文件：

```sh
python3 build_rickyos_wallpapers.py --sources sources --output . --tag v1.0.0
```

图片为 RickyOS 原创，使用 AI 图像生成工具制作。
