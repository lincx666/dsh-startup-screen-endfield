# MOD-NOTES — 工业终端风格改造说明

> 基于上游 `dsh-startup-screen` v1.3.0 的二次创作。

## 配色

```css
--dsu-bg:     #101214   哑光黑
--dsu-ink:    #e8edee   冷白
--dsu-accent: #e5b80b   琥珀
--dsu-glitch-a: #e04a3f 警示红
--dsu-glitch-b: #2ee6c8 青绿（仅故障/扫描）
```

## 修改的文件

| 文件 | 改动 |
|---|---|
| `lib/splash.css` | 追加配色、网格、警示斜纹、切角、扫描、频谱、鲸鱼仪器框等样式块 |
| `lib/splash.js` | 五幕文案、终端滚屏、SYNC 读数、频谱条、BGM 模块、第五幕交互 |
| `lib/index.js` | 新增 `bgm` / `bgmVolume` / `bgmChorusAt` 配置项与默认值 |

> 路由前缀、模块注册 id、存储键、配置文件路径全部保持原版不变，
> 以保证与上游结构兼容。

## 背景音乐

- 音频文件 `lib/assets/bgm.mp3` **不随仓库分发**
- 播放走原版的 `/asset/bgm.mp3` 路由
- 播放器先 `fetch` 成 Blob 再 `URL.createObjectURL`，避免服务端无 Range 导致 `seekable=0`
- 配置项：
  - `bgm`: 开关
  - `bgmVolume`: 音量（0–1）
  - `bgmChorusAt`: 副歌起点（秒，默认 30）

## 还原

如需回到纯原版，使用 `dsh-startup-screen-orig-pristine.zip`（不在本仓库内）。
