# 部署说明

## GitHub Pages 部署

1. 创建 GitHub 仓库，例如：`mianya-interview-agent`。
2. 将项目所有文件上传到仓库根目录。
3. 进入仓库 `Settings` -> `Pages`。
4. 在 `Build and deployment` 中选择：
   - Source: Deploy from a branch
   - Branch: main
   - Folder: /root
5. 点击 Save。
6. 等待 GitHub Pages 自动部署。

部署完成后，访问地址通常为：

```text
https://你的GitHub用户名.github.io/mianya-interview-agent/
```

## 本地预览

```bash
python3 -m http.server 3000
```

然后访问：

```text
http://localhost:3000
```

## 上线前替换项

请将以下占位内容替换为真实信息：

- `zzrdezuiai@163.com`
- `https://github.com/zzrdezuiai-tech/interview-agent`
- `https://github.com/zzrdezuiai-tech/interview-agent`
