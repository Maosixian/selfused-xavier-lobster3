# 广告数据同步到飞书多维表格

## 项目简介
此项目帮助你将Meta Ads (Facebook/Instagram) 和 Google Ads 数据自动同步到飞书多维表格中。

## 支持的平台
1. **Meta Ads (Facebook/Instagram)** - 通过OAuth授权
2. **Google Ads** - 需要开发者令牌和OAuth
3. **飞书多维表格** - 通过飞书API写入

## 准备工作

### 1. 环境要求
- Python 3.8+
- pip包管理器

### 2. 安装依赖
```bash
pip install facebook-business google-ads feishu-client pandas
```

### 3. 平台权限准备

#### Meta Ads权限
1. 访问 [Facebook开发者平台](https://developers.facebook.com/)
2. 创建应用（选择"企业业务"类型）
3. 添加"Marketing API"产品
4. 获取App ID和App Secret
5. 添加系统用户或获取用户访问令牌

#### Google Ads权限
1. 访问 [Google Cloud Console](https://console.cloud.google.com/)
2. 创建项目并启用"Google Ads API"
3. 创建OAuth 2.0凭证
4. 申请开发者令牌
5. 获取刷新令牌

#### 飞书权限
1. 已有飞书多维表格
2. 获取App Token（从URL中提取）
3. 创建应用获取权限

## 快速开始

### 方案A：完整Python脚本（推荐）
运行 `sync_ads_to_feishu.py` 脚本，按照提示完成授权和数据同步。

### 方案B：分步操作
1. 获取访问令牌
2. 运行数据查询
3. 手动写入表格

## 数据字段映射

### Meta Ads → 表格字段
- `spend` → `FB花费`
- `purchase` → `FB订单`
- `purchase_value` → `FB订单金额`
- `clicks` → `FB点击量`
- `impressions` → `FB展示`
- `add_to_cart` → `FB加购次数`
- `initiate_checkout` → `FB Checkout`

### Google Ads → 表格字段
- `cost` → `GG花费`
- `conversions` → `GG订单`
- `conversion_value` → `GG订单金额`
- `clicks` → `GG点击量`
- `impressions` → `GG展示`

## 配置说明
编辑 `config.yaml` 文件设置：
- 飞书多维表格信息
- 广告账户ID
- 数据时间范围
- 同步频率

## 自动化部署
- 支持cron定时任务
- Docker容器化
- 云函数部署

## 故障排除
常见问题请查看 `TROUBLESHOOTING.md`

## 联系我们
如有问题，请联系OpenClaw助手