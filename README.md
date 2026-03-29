# ZhiWei Index

知微官方 Marketplace 索引仓库。

仓库地址：

- `ZhiWei-index`: `https://github.com/ntygod/ZhiWei-index`
- `ZhiWei-plugins`: `https://github.com/ntygod/ZhiWei-plugins`
- `ZhiWei`: `https://github.com/ntygod/ZhiWei`

## 角色

这个仓库只负责发布 Marketplace 可消费的 `index.json`。

它不再承载：

- 官方插件源码
- 官方 connector 工程
- 手工维护的渠道清单文档

## 索引来源

当前索引由 `ZhiWei-plugins` 仓库导出：

- 渠道插件条目来自 `channels/*/channel-plugin.json`
- 旧索引中的非渠道条目会被保留
- 渠道条目由自动化流程覆盖更新

## 当前约定

- `index.json` 是 Marketplace 主入口
- `CHANNEL` 条目由插件仓库自动生成
- 其他类型条目可在过渡期继续保留

## 维护方式

正常情况下不直接手工修改渠道条目。

如果需要本地重新生成索引，应在 `ZhiWei-plugins` 仓库执行：

```powershell
pwsh -NoProfile -File .\tools\export-channel-index.ps1 `
  -ExistingIndexPath ..\ZhiWei-index\index.json `
  -OutputPath ..\ZhiWei-index\index.generated.json
Move-Item ..\ZhiWei-index\index.generated.json ..\ZhiWei-index\index.json -Force
```
