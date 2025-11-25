---
title: "多页面博客系统上线"
date: 2025-11-25T10:00:00+08:00
draft: false
tags: ["Kubernetes", "ConfigMap", "Nginx"]
---
今天实现了一个重要的里程碑！我成功地使用 Kubernetes ConfigMap 挂载了多个 HTML 文件，
现在可以实现真正的多页面导航了。
<!--more-->
点击顶部导航栏的"关于我"，你可以跳转到另一个页面。这两个页面都是通过同一个 ConfigMap 
挂载到 Nginx 容器中的。
## ConfigMap 的多文件实践
使用以下命令可以将多个文件打包进一个 ConfigMap：
\`\`\`bash
kubectl create configmap myblog-html \\
  --from-file=index.html=index.html \\
  --from-file=about.html=about.html
\`\`\`
当这些文件被挂载到 `/usr/share/nginx/html` 时，Nginx 会自动提供这些静态文件的访问服务。
