# 网页转 PDF · 中文路径避坑

Windows 上用 Edge 无头模式把本地 HTML 导成 PDF，专门解决**中文路径静默失败**：命令返回 0、却生成 0 字节文件，而且不报错。

## 三个必踩的坑

1. 源文件路径含中文时，直接把路径传给 Edge 会失败 → 先把 HTML 复制到无中文的临时路径再打印。
2. 不指定 `--user-data-dir` 会和用户正在运行的 Edge 冲突 → 用独立 profile 目录。
3. 打印后不校验输出 → 用 `head -c 5` 确认文件头是 `%PDF-`。

完整命令和验证步骤见 [SKILL.md](SKILL.md)。

## 安装

把本目录复制到 `~/.workbuddy/skills/edge-html-to-pdf/`。

## 环境

Windows + Microsoft Edge；无第三方依赖。
