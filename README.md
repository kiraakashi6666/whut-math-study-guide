# WHUT 数学er 学习指南

这是一个使用 Zensical 生成的中文文档网站。正文全部保存在 `docs/` 中，可以继续使用 Markdown 修改。

- [在线阅读](https://kiraakashi6666.github.io/whut-math-study-guide/)
- [GitHub 仓库](https://github.com/kiraakashi6666/whut-math-study-guide)

## 第一次运行

在项目目录打开终端，依次运行：

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install zensical
python3 -m zensical serve
```

然后在浏览器打开 <http://localhost:8000>。按 `Control + C` 可以停止预览服务器。

## 以后修改文章

1. 打开 `docs/` 下对应的 `.md` 文件。
2. 使用 Markdown 修改内容并保存。
3. 在项目目录运行：

   ```bash
   source .venv/bin/activate
   python3 -m zensical serve
   ```

4. 浏览器中的网页会随文件保存自动更新。

## 新增文章

先在 `docs/` 的相应目录中新建 Markdown，例如：

```text
docs/gpa/new-topic.md
```

文件第一行写文章标题：

```markdown
# 新主题
```

随后在 `zensical.toml` 的 `nav` 列表中加入页面路径，页面才会出现在左侧导航中。

## 调整文章分区

- 只修改正文或增减 `##` 小标题：直接编辑对应 Markdown，不需要修改导航。
- 把文字移动到另一个现有页面：剪切到目标 Markdown，并检查原有链接。
- 新建、删除、移动或重命名 Markdown：同时修改 `zensical.toml` 中的 `nav` 路径。
- 修改完成后先运行测试和本地预览，再提交到 GitHub。

## 与协作者共同更新

每个人开始修改前先拉取远端更新，完成后提交并推送。推荐各自在独立分支修改，通过 Pull Request 合并到 `main`；合并后 GitHub Actions 会自动重新构建并发布网站。

如果两个人直接修改同一篇 Markdown 的同一位置，Git 可能要求手动解决冲突；修改不同页面通常不会互相影响。

## 插入图片

建议将图片放在使用它的 Markdown 文件旁边，并使用简短、可读的英文文件名，然后通过相对路径引用：

```markdown
![图片说明](campus-map.png)
```

如果图片放在其他目录，需要根据 Markdown 文件的位置调整相对路径。

## 构建网站

发布或检查前运行：

```bash
source .venv/bin/activate
python3 -m zensical build
```

生成的静态网页位于 `site/`。`site/`、`.venv/` 和 Python 缓存均为本地生成内容，不需要上传。

## 内容位置

- `docs/index.md`：首页。
- `docs/introduction.md`：引言。
- `docs/gpa/`：日常学习、课外学习与期末备考。
- `docs/postgraduate/`：保研须知、简历和 PPT、套磁、笔面经验与其他事项。
- `docs/campus-life/`：地点、社交、师生关系、WHUT 网站与入党。
- `zensical.toml`：网站名称、语言、外观和左侧导航。

## 自动检查

修改目录或链接后，可以运行：

```bash
python3 -m unittest tests/test_site_structure.py
```

检查会确认所有导航页面存在、中文配置正确，并检查失效的本地图片引用。

## 许可

本项目原创文字和图片采用 [CC BY-NC-SA 4.0](LICENSE.md) 许可：允许在署名的前提下用于非商业目的，也允许修改，但修改后的内容必须继续采用相同许可。
