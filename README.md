# thinkplus 移动硬盘修复记录

## 设备信息

| 项目 | 内容 |
|------|------|
| 硬盘 | thinkplus 移动硬盘 |
| 容量 | 1TB |
| 当前文件系统 | exFAT |
| 分区名 | thinkplus |
| 设备路径 | `/dev/disk5s1` |
| 挂载路径 | `/Volumes/thinkplus` |

## 问题现象

1. 插入硬盘后 Finder 无响应、崩溃
2. 拔掉硬盘后 Finder 立即恢复正常
3. Mac 曾因硬盘卡死而强制重启
4. 命令行读取部分目录时挂起：`du`、`find`、`diskutil unmountDisk` 均超时
5. 尝试用 rclone 上传到 Google Drive 时速度为 0，无法读取

## 已尝试的修复（Mac 端）

| 操作 | 结果 |
|------|------|
| 重启 Finder | 无效 |
| 强制卸载硬盘 | 超时失败 |
| rclone 备份到 Google Drive | 速度为 0，失败 |
| 等待 macOS 后台自动修复 | 几小时后仍无改善 |

## 当前判断

硬盘文件系统已损坏，macOS 对损坏 exFAT 的修复能力有限。最可靠的修复方式是在 Windows 上运行 `chkdsk`。

## 推荐修复步骤（网吧/Windows 电脑）

1. 将硬盘插入 Windows 电脑
2. 按 `Win + R`，输入 `cmd`，回车打开命令提示符
3. 查看硬盘盘符（例如 `E:`）
4. 运行修复命令：

   ```cmd
   chkdsk E: /f
   ```

5. 等待扫描并修复完成
6. 修复完成后，立即将重要文件复制到电脑本地或上传网盘备份
7. 备份完成后，建议将硬盘格式化为 **exFAT** 或 **NTFS**

## 重要文件清单（待备份）

- `以前`
- `资源`
- `iphone`
- `iCloud照片.7z`
- `2025双旦北海道东京`
- `日本行`
- `堆栈练习`

## 备份目标

- Google Drive：5TB 空间，已配置 rclone（但因硬盘读取失败未成功上传）
- 夸克网盘：3.3TB 剩余空间

## 后续建议

- 修复并备份后，格式化硬盘为 exFAT（兼容 Mac 和 Windows）
- 避免在数据传输过程中触碰硬盘线缆
- 定期备份重要数据
