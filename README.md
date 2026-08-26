# BreezeSavings（攒钱计划 iOS）

原生 SwiftUI 第一版，不使用 WebView/H5。

## 已完成
- 首页：目标、进度、收入/支出、最近记录
- 记账：收入/支出新增、筛选、左滑删除
- AI 管家：连接 `/api/ai`，支持自然语言记账；AI 返回 `parsed_records` 后写入 `/api/records`
- 我的：目标金额、计划月份、预算概览
- API：兼容原项目 `/api/records`、`/api/finance`、`/api/ai`
- GitHub Actions：macOS 云端生成 Xcode 工程并做无签名编译检查

## 你必须修改的一处
打开 `BreezeSavings/Services/APIClient.swift`，把：
`https://breeze-bid.pages.dev`
换成当前 Breeze 网站的 HTTPS 域名（不要在 App 内放 DeepSeek API Key）。

## 没有 Mac 的使用方式
1. 把整个目录上传 GitHub。
2. GitHub Actions 会在 macOS runner 安装 XcodeGen，生成 `BreezeSavings.xcodeproj` 并编译检查。
3. 后续上传 TestFlight 时，再增加 Apple Developer / App Store Connect 的签名配置与上传步骤。

## 安全
DeepSeek Key 继续保存在 Cloudflare 服务端环境变量中；iOS 客户端只访问你的后端 API。
