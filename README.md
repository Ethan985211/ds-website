# DS 产品官网

DS(Desktop system Agent)产品官网,独立目录,与桌面应用仓库(`Desktop system/`)分离,避免误打包进应用产物。

## 结构

```
ds-website/
├── index.html      # 官网单页(自包含:内联 CSS/JS)
├── 404.html        # 404 页(Cloudflare Pages 自动识别)
├── robots.txt      # 允许抓取 + 指向 sitemap
├── sitemap.xml     # 单页 sitemap
├── assets/
│   ├── ds-logo.webp    # 品牌 Logo(160px,由 ds-logo.png 转换,页面只用这个)
│   ├── ds-logo.png     # Logo 原图(2048px,源文件,页面不引用)
│   └── og-cover.png    # 1200×630 社交分享封面
└── README.md
```

## 本地预览

直接双击 `index.html` 即可,或:

```
python -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 部署(GitHub + Cloudflare Pages,已上线)

线上地址:`https://desktopsystem.cc.cd`(生产,自动构建)

### 更新站点(改完即上线)

改 `index.html` / `assets/` 后推送到 GitHub 即可,Cloudflare Pages 自动重新构建部署:

```
git add -A
git commit -m "update"
git push origin main
```

几分钟后访问 `https://desktopsystem.cc.cd` 生效。

### 基础设施(已配置,勿改)

- 仓库:`github.com/Ethan985211/ds-website`(分支 `main`)
- 托管:Cloudflare Pages 项目 `ds-website`,默认域名 `ds-website-2qw.pages.dev`
- 域名:`desktopsystem.cc.cd`,DNS 托管在 Cloudflare(NS: `dara/jim.ns.cloudflare.com`),CNAME `@ → ds-website-2qw.pages.dev`(已代理)
- 域名注册仍在 DNSHE(到期 2027-09-18),NS 已指向 Cloudflare

## 修改

改 `index.html` 后,用 html skill 自检脚本复核:

```
python <skill_dir>/scripts/shot.py index.html
```

截图输出在 `_shots/`(非交付产物)。

## 下载按钮怎么上线 / 下线

`index.html` 里的 `DS_RELEASE` 是全站唯一真相,包名、体积、按钮状态都由它派生:

```js
var DS_RELEASE = {
  name: 'DS-Desktop-0.3.0-beta.1-setup.exe',  // 显示的文件名
  size: '~115 MB',                            // 显示的体积
  url:  '',                                   // 安装包直链;为空 = 未开放下载
  mirror: ''                                  // 可选镜像前缀,如 https://ghproxy.net/
};
```

- `url` 为空:按钮显示「即将发布」,点击弹提示,不会静默失败。
- 填入 `url` 即恢复下载,无需改文案。
- 换版本只改这一处,下载区三处文案不会打架。

