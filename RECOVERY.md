# 恢复、部署与迁移指南

## 误卸载恢复办法
1. 确保已安装git
2. 克隆仓库：`git clone <仓库地址> ~/.openclaw/workspace`
3. 进入目录：`cd ~/.openclaw/workspace`
4. 安装依赖：`npm install`
5. 恢复配置：复制备份的`.env`、`config.yaml`文件到工作目录
6. 启动服务：`openclaw gateway start`

## Docker部署方法
```dockerfile
FROM openclaw/openclaw:latest
WORKDIR /app
COPY . .
RUN npm install
ENV OPENCLAW_CONFIG_PATH=/app/config.yaml
EXPOSE 18789
CMD ["openclaw", "gateway", "start"]
```
构建命令：`docker build -t openclaw-agent .`
运行命令：`docker run -p 18789:18789 -v /path/to/config:/app/config.yaml openclaw-agent`

## 迁移办法
1. 停止当前服务：`openclaw gateway stop`
2. 备份所有数据：`tar -czvf openclaw-backup.tar.gz ~/.openclaw/`
3. 将备份文件传输到新机器
4. 在新机器解压：`tar -xzvf openclaw-backup.tar.gz -C ~/`
5. 启动服务：`openclaw gateway start`
6. 验证功能正常运行
