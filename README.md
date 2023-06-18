# [bilibili 视频封面图](https://bb-embed.zjffun.com/)

在 GitHub 中嵌入 bilibili 视频时添加视觉提示的工具。

## 示例

嵌入 [VS Code 代码片段（Snippets）管理\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1jS4y1w7SW?spm_id_from=333.999.0.0) 这个视频，使用：

```
[![](https://i1.hdslb.com/bfs/archive/9a32c55b90ac9485d02dc1a50dc1fa94d12b3111.jpg@640w_400h_1c.webp)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)
```

外观是这样：

[![](https://i1.hdslb.com/bfs/archive/9a32c55b90ac9485d02dc1a50dc1fa94d12b3111.jpg@640w_400h_1c.webp)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)

使用此工具自动添加视觉提示

```
[![](https://bb-embed.zjffun.com/embed?v=BV1jS4y1w7SW)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)
```

外观是这样：

[![](https://bb-embed.zjffun.com/embed?v=BV1jS4y1w7SW)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)

## 常见问题

如果发现 2022 年 12 月之前的图片错误，将图片地址的 `https://bb-embed.herokuapp.com/` 更换为 `https://bb-embed.zjffun.com/` 即可。

## 本地开发

```sh
docker compose -f docker-compose.dev.yml up --build
```

## 部署

```sh
sudo docker run -d --restart=always --name bb-embed -p 8848:8000 zjffun/bb-embed
```

NGINX 配置:

```bash
sudo cat <<'EOF' > /etc/nginx/sites-enabled/bb-embed-zjffun-com
server {
    server_name bb-embed.zjffun.com;
    listen 80;

    location / {
        proxy_pass http://localhost:8848;
    }
}
EOF
```
