# [bilibili 视频封面图](https://bb-embed.herokuapp.com/)

在 GitHub 中嵌入 bilibili 视频时添加视觉提示的工具。

## 本地运行应用程序

- 确保已安装 [nix](https://nixos.org/download.html)
- 克隆仓库，并 `cd` 进入
- 运行 `nix-shell`
- 运行 `gunicorn -w 4 -b 0.0.0.0:8080 wsgi:app` 并访问 http://localhost:8080/

## 示例

嵌入 [VS Code 代码片段（Snippets）管理\_哔哩哔哩\_bilibili](https://www.bilibili.com/video/BV1jS4y1w7SW?spm_id_from=333.999.0.0) 这个视频，使用：

```
[![](https://i1.hdslb.com/bfs/archive/9a32c55b90ac9485d02dc1a50dc1fa94d12b3111.jpg@640w_400h_1c.webp)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)
```

外观是这样：

[![](https://i1.hdslb.com/bfs/archive/9a32c55b90ac9485d02dc1a50dc1fa94d12b3111.jpg@640w_400h_1c.webp)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)

使用此工具自动添加视觉提示

```
[![](https://bb-embed.herokuapp.com/embed?v=BV1jS4y1w7SW)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)
```

外观是这样：

[![](https://bb-embed.herokuapp.com/embed?v=BV1jS4y1w7SW)](https://player.bilibili.com/player.html?aid=683633468&bvid=BV1jS4y1w7SW&cid=711074429&page=1)

## 部署和托管

使用 [heorku](https://heroku.com/) 进行部署。该应用程序托管在 https://bb-embed.herokuapp.com/
