# GitHub Trending Daily Reporter

自动获取GitHub官方Trending榜单并发送到Telegram的GitHub Actions工作流。

## ✨ 功能特性

- ✅ **每日自动运行**：UTC时间9:00（北京时间17:00）
- ✅ **手动触发**：随时在GitHub页面点击运行
- ✅ **真实Trending**：直接解析GitHub Trending页面
- ✅ **Telegram推送**：格式化消息，支持长文分割
- ✅ **错误处理**：备用数据机制，失败重试
- ✅ **完全免费**：使用GitHub Actions免费额度

## 🚀 快速部署

### 1. Fork本仓库
点击右上角 "Fork" 按钮创建你的副本。

### 2. 配置Secrets
在仓库设置中添加以下Secrets：
- `TELEGRAM_BOT_TOKEN` - 你的Telegram Bot Token
- `TELEGRAM_CHAT_ID` - 接收消息的Chat ID
- `TAVILY_API_KEY` (可选) - Tavily API密钥，用于背景搜索

### 3. 立即测试
在仓库的 "Actions" 标签页：
1. 选择 "Daily GitHub Trending Report"
2. 点击 "Run workflow"
3. 选择分支并运行

## ⚙️ 配置说明

### 定时触发
默认每天UTC时间9:00运行，可在 `.github/workflows/daily-trending.yml` 修改cron表达式：

```yaml
schedule:
  - cron: '0 9 * * *'  # 每天9:00 UTC
```

### 环境变量
| 变量名 | 必需 | 说明 |
|--------|------|------|
| `TELEGRAM_BOT_TOKEN` | ✅ | Telegram Bot Token |
| `TELEGRAM_CHAT_ID` | ✅ | 接收消息的Chat ID |
| `TAVILY_API_KEY` | ❌ | Tavily API密钥（背景搜索） |
| `GITHUB_TOKEN` | ❌ | GitHub Token（自动提供） |

## 📊 输出示例

```
🔥 GitHub官方Trending榜单 2026年02月12日

📌 通过GitHub Actions自动生成

🥇 第1名: tambo-ai/tambo
⭐ 总星星: 279 | 📈 今日增长: +279 | 🍴 分叉: 0
📝 语言: TypeScript
📋 描述: Generative UI SDK for React
🔗 链接: https://github.com/tambo-ai/tambo
────────────────────────────────────────
```

## 🔧 本地测试

### 安装依赖
```bash
# 无需额外依赖，仅需Python 3.8+
python3 --version
```

### 运行测试
```bash
# 设置环境变量
export TELEGRAM_BOT_TOKEN="你的Bot Token"
export TELEGRAM_CHAT_ID="你的Chat ID"

# 运行脚本
python3 github_trending_actions.py
```

## 📈 使用统计

- **每月免费额度**：2000分钟
- **每次运行时间**：约1-3分钟
- **每日运行消耗**：约3分钟
- **每月消耗**：约90分钟（远低于2000分钟限制）

## 🛠️ 故障排除

### 常见问题
1. **脚本运行失败**
   - 检查Secrets配置是否正确
   - 查看Actions运行日志

2. **Telegram消息未收到**
   - 确认Bot已启动且Chat ID正确
   - 检查Bot是否有发送消息权限

3. **Trending数据获取失败**
   - GitHub页面结构可能变化，需要更新解析逻辑
   - 脚本有备用数据机制

### 查看日志
在仓库的 "Actions" → "Daily GitHub Trending Report" → 点击具体运行 → 查看日志。

## 📄 文件结构

```
.
├── .github/workflows/
│   └── daily-trending.yml    # GitHub Actions工作流配置
├── github_trending_actions.py # 主脚本（适配Actions环境）
├── README.md                 # 说明文档
└── requirements.txt          # Python依赖（暂无）
```

## 🤝 贡献

欢迎提交Issue和Pull Request：
- 报告Bug
- 提出新功能建议
- 改进代码或文档

## 📝 许可证

MIT License