# DS 产品官网

DS(Desktop system Agent)产品官网,独立目录,与桌面应用仓库(`Desktop system/`)分离,避免误打包进应用产物。

## 结构

```
ds-website/
├── index.html      # 官网单页(自包含:内联 CSS/JS)
├── assets/
│   └── ds-logo.png # 品牌定稿 Logo(墨绿底白标「DS 交错标」)
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
