# 更新日志

## [1.0.3] - 2024-12-26

### 🎨 新增功能
- **可选玩家头像显示**
  - 新增 `showPlayerAvatar` 配置项（默认为 `false`）
  - 支持在以下命令中控制是否显示玩家皮肤图片：
    - `mcid query` / `mcid query [目标用户]`
    - `mcid bind` / `mcid bind <用户名> [目标用户]`
    - `mcid change` / `mcid change <用户名> [目标用户]`
    - `mcid finduser <用户名>`

### 🔧 功能改进
- **优化 reset 命令**
  - 现在支持直接删除任意服务器ID的白名单记录
  - 无需验证服务器是否存在于当前配置中
  - 便于清理已从配置中删除但数据库中仍存在的服务器ID

### 🆕 新增命令
- **`mcid whitelist resetall`** (主人权限)
  - 一键清理所有未在服务器配置列表中的无效白名单ID
  - 提供详细的清理报告，包括处理记录数、更新记录数、移除的无效条目数
  - 列出所有发现的无效服务器ID

- **`mcid tag deleteall <标签名>`** (主人权限)
  - 一键删除所有用户的指定标签
  - 支持批量操作，提供详细的操作结果统计
  - 安全的权限控制，仅主人可执行

### ⚡ 性能优化
- **改进 RCON 排队机制**
  - `mcid whitelist addall` 命令现按绑定时间排序处理（早绑定用户优先）
  - 移除并发处理，改为真正的队列机制，确保每个RCON命令等待上一个完成后再继续
  - 增加处理间隔（1秒），避免RCON服务器过载
  - 降低并发冲突风险，提高批量操作稳定性

### 🛡️ 安全改进
- **增强配置访问防护**
  - 所有 `config.showPlayerAvatar` 访问都改为 `config?.showPlayerAvatar`
  - 提高代码对异常配置状态的容错性
  - 防止因配置对象不存在导致的运行时错误

### 📝 文档更新
- 更新 README.md，添加新功能的使用说明
- 更新 package.json 描述，反映最新功能特性
- 完善配置项说明文档

---

## [1.0.2] - 2024-12-xx

### 新增功能
- 支持解析 `<at id="..."/>` 格式的@用户字符串
- 改进用户ID处理：增强对不同@用户格式的兼容性
- 添加构建发布脚本：新增自动化构建和发布的bat脚本

---

## [1.0.1] - 2024-12-xx

### 修复
- 修复Logger名称：将内部日志记录器名称从'bind-mcid'更新为'mcid-bot'
- 代码清理：确保所有内部引用都使用正确的项目名称

---

## [1.0.0] - 2024-12-xx

### 初始发布
- 支持Minecraft账号绑定和管理功能
- 支持多服务器白名单管理
- 支持用户标签系统，便于批量管理
- 支持批量白名单操作
- 支持管理员权限控制
- 支持RCON连接管理
- 支持消息自动撤回
- 支持文本前缀触发指令
- 完整的错误处理和日志系统 