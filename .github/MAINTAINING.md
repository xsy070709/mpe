# 讲义维护说明

讲义正文以 [`docs/`](../docs/) 下的 Markdown 文件为准。网页版和离线 PDF 按 [`nav.yml`](../nav.yml) 中的章节顺序构建。

## 整理板书

- 先按授课顺序归并同一节的板书，再写成可独立阅读的讲义。保留定义、定理的适用条件、关键推导、例题和结论。可以补齐读者理解所需的中间步骤。
- 沿用本章的记号和公式约定。遇到模糊字迹，先用上下文和相邻公式核对。仍有歧义的地方单独记下并确认后再发布。
- 讲义正文和仓库首页供读者使用。识别疑点、待核事项和编辑记录留在工作记录或提交历史。首次发布章节正文时，同步更新首页和 README 中对应的章节状态。

## 更新章节

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

发布前对照板书核对公式、定理条件和例题。网页检查章节导航、公式排版和链接。PDF 检查目录、书签和实际用到的跨章跳转。发布后打开网页版和固定的 PDF 下载地址，确认两者均可访问。
