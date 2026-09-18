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

## 部署(域名 desktopsystem.cc.cd)

1. **DNS 解析**:在域名服务商控制台添加解析记录,将 `desktopsystem.cc.cd` 指向托管平台(二选一):
   - Cloudflare Pages / GitHub Pages:A 记录指向平台提供的 IP,或 CNAME 指向平台域名
   - 国内对象存储(如阿里云 OSS + CDN):A/CNAME 指向存储空间
2. **上传**:把 `index.html` 与 `assets/` 上传到托管平台(静态站点,无需后端)。
3. **HTTPS**:托管平台开启 SSL 证书(Cloudflare 免费证书或平台自动签发)。
4. **验证**:访问 `https://desktopsystem.cc.cd` 确认首页、Logo、favicon 正常。

> 注:图片引用为相对路径(`assets/ds-logo.png`),发布时必须连同 `assets/` 目录一起上传,否则 Logo 不显示。

## 修改

改 `index.html` 后,用 html skill 自检脚本复核:

```
python <skill_dir>/scripts/shot.py index.html
```

截图输出在 `_shots/`(非交付产物)。
