# RickyOS 默认待机图片

RickyOS（MindReset Read Pico 固件）在「应用 → 待机显示」和「设置 → 电源与待机」里提供「下载默认图片」，从这里下载到 `/images/待机图片/`。

v1.4.0 包含 17 张待机图片（与 v1.3.0 相同，全部是浅色画面：RickyOS「休息一下」品牌画面、Ricky 和小狗的 logo 风格线稿、涂鸦配标语、绘本插画），以及新增的 16 张透明壁纸。

| 文件 | 设备上的名字 |
| --- | --- |
| `wallpapers/00-rest.png` | 休息一下 |
| `wallpapers/31-reading-together.png` | 一起读书 |
| `wallpapers/32-dog-nap.png` | 小狗午睡 |
| `wallpapers/33-moon-reading.png` | 月亮上读书 |
| `wallpapers/34-dog-fetch.png` | 叼书小狗 |
| `wallpapers/35-book-nap.png` | 书本盖脸 |
| `wallpapers/36-peek.png` | 书后探头 |
| `wallpapers/21-one-more-page.png` | 先看一页 |
| `wallpapers/22-do-not-disturb.png` | 别催 |
| `wallpapers/23-battery-full.png` | 电量充足 |
| `wallpapers/24-slow-reading.png` | 慢慢读 |
| `wallpapers/25-stay-home.png` | 不出门 |
| `wallpapers/26-fish-culture.png` | 摸鱼 |
| `wallpapers/12-bear-balloon.png` | 小熊的气球 |
| `wallpapers/13-whale-clouds.png` | 云上鲸鱼 |
| `wallpapers/14-hedgehog-library.png` | 刺猬去图书馆 |
| `wallpapers/15-fox-tree.png` | 树上的狐狸 |

透明壁纸（RickyOS 1.2.0 起下载到 `/images/透明壁纸/`，待机时叠在当前页面上）：

| 文件 | 设备上的名字 |
| --- | --- |
| `wallpapers/s01-tear.png` | 破纸而出 |
| `wallpapers/s02-peek-up.png` | 巨型探头 |
| `wallpapers/s03-belly-up.png` | 累趴了 |
| `wallpapers/s04-squish.png` | 贴脸 |
| `wallpapers/s05-blanket.png` | 盖被子 |
| `wallpapers/s06-sleep.png` | 趴着睡 |
| `wallpapers/s07-hang.png` | 扒住顶边 |
| `wallpapers/s08-peek-side.png` | 侧边偷看 |
| `wallpapers/s09-paws.png` | 脚印 |
| `wallpapers/s10-gang-pile.png` | 动物帮睡成一堆 |
| `wallpapers/s11-gang-peek.png` | 动物帮一排探头 |
| `wallpapers/s12-gang-tower.png` | 动物帮叠罗汉 |
| `wallpapers/s13-badge.png` | 工牌 |
| `wallpapers/s14-credits.png` | 片尾字幕 |
| `wallpapers/s15-wordmark.png` | 竖排字标 |
| `wallpapers/s16-stamp.png` | 印章 |

透明壁纸是带透明通道的 684×1216 灰阶 PNG。清单里的 `stickers` 列表只有 1.2.0 及以后的固件会读取，旧固件只读 `items`，不受影响。

- `wallpapers/*.png`：684×1216，4 位 16 级灰阶调色板 PNG（白底图压缩率高，16 张共约 1.1 MB），对应 Read Pico 的 16 级灰度屏；设为壁纸时设备把它转成 8 位灰度 BMP，16 级灰度不丢。
- `wallpapers.json`：下载清单，文件地址指向 GitHub Release；`mirror.json`：同一份清单，文件地址经 jsDelivr 镜像本仓库的 `wallpapers/`。两份清单的 `mirrors` 列出其他存放相同文件的地址，某个文件下载失败时设备会依次换用。
- `sources/`：原图（1024×1536）。`build_rickyos_wallpapers.py` 把原图裁成 9:16、缩放并抖动到 16 级灰阶；logo 风格的线稿收进画面中上部，涂鸦图的标语用得意黑（Smiley Sans，OFL，见 `sources/OFL-SmileySans.txt`）排在图下，都避开右下角的待机时间卡片：

```sh
python3 build_rickyos_wallpapers.py --sources sources --output . --slogan-font SmileySans-Oblique.otf --tag v1.3.0
```

图片为 RickyOS 原创，使用 AI 图像生成工具制作；Ricky 和小狗来自 RickyOS 的 logo；「休息一下」直接取自固件在原生分辨率下绘制的待机画面。
