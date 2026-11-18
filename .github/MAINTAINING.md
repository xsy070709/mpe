# 讲义维护说明

讲义正文以 [`docs/`](../docs/) 下的 Markdown 文件为准。网页版和离线 PDF 按 [`nav.yml`](../nav.yml) 中的章节顺序构建。

## 维护讲义

在 `docs/` 下新增章节文件，并在 `nav.yml` 中登记。每章使用一个一级标题，章内依次使用二、三级标题。行内公式写作 `$...$`，独立公式写在单独的 `$$` 区块中。跨章引用使用相对 Markdown 路径和网页标题锚点。图片放在 `docs/assets/` 下，通过相对路径引用。

## 本地构建

在 Debian 或 Ubuntu 上安装 Pandoc、XeLaTeX 和中文字体后构建。网页公式由 MathJax 渲染，离线 PDF 嵌入公式与中文字体。

```sh
sudo apt-get install pandoc texlive-xetex texlive-lang-chinese texlive-latex-extra texlive-fonts-recommended fonts-noto-cjk lmodern
python -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
python scripts/build_pdf.py
mkdir -p docs/downloads
cp output/pdf/mathematical-physics-equations-notes.pdf docs/downloads/
mkdocs build --strict
mkdocs serve
```

## 发布

在仓库的 **Settings → Pages → Build and deployment** 中，确认 **Source** 为 **GitHub Actions**。推送 `main` 或在 Actions 中从 `main` 手动运行 **Deploy notes and PDF**，会先构建和校验 PDF 与网页，再部署 GitHub Pages，并用同一份文件更新 `pdf-latest` Release。PDF 下载地址固定。
