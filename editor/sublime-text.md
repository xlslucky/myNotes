# sublime 编辑器

## 下载
[sublime 官网](http://www.sublimetext.com/)

## plugin

> ctrl(command) + shift + p

* AutoFileName
* Babel
* BracketHighlighter
* ChineseLocalizations
* Emmet
* HTML-CSS-JS Prettify
* SCSS
* JavaScript Completions
* Material Color Scheme
* Material Theme

## Mac上命令行启动编辑器

```shell
$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin 

$ sudo ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

此时就可以通过`subl .`在sublime中打开当前文件夹

## 配置文件
```json
{
  "bold_folder_labels": true,
  "caret_style": "smooth",
  "theme": "Material-Theme.sublime-theme",
  "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
  "default_line_ending": "unix",
  "disable_tab_abbreviations": true,
  "draw_minimap_border": true,
  "draw_white_space": "all",
  "file_exclude_patterns":
  [
    ".DS_Store",
    "Desktop.ini",
    "*.pyc",
    "._*",
    "Thumbs.db",
    ".Spotlight-V100",
    ".Trashes"
  ],
  "folder_exclude_patterns":
  [
    ".*",
    "build",
    "node_modules",
    "bower_components"
  ],
  "font_options":
  [
    "gray_antialias"
  ],
  "font_size": 16,
  "highlight_line": true,
  "ignored_packages":
  [
    "Markdown",
    "Vintage"
  ],
  "indent_guide_options":
  [
    "draw_normal",
    "draw_active"
  ],
  "line_padding_bottom": 5,
  "line_padding_top": 5,
  "margin": 2,
  "tab_size": 2,
  "translate_tabs_to_spaces": true
}

```