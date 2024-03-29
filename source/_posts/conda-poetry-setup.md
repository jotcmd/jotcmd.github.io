---
title: conda+poetry快速setup开源项目
date: 2024-02-05 16:04:50
tags:
---

以`Search with Lepton`项目为例
1. 先下载：
  ```bash
  git clone https://github.com/leptonai/search_with_lepton/
  ```
2. 然后先切base环境：
  （思路是，不涉及cuda的项目，就基于conda base然后poetry venv轻量化了）  
  ```bash
  conda activate base
  pip3 add poetry  # base 环境如果没有poetry也是不行的
  poetry config virtualenvs.create true  # 这步很关键，不复用conda的环境，而是新建venv
  ```
3. 然后setup poetry环境： 
  ```bash
  poetry init
  poetry install
  poetry shell
  ```
4. 顺利的话，一个专门for这个项目的，干净清爽的python环境，就ok了。Enjoy！
5. 然后，和vscode联动的时候，`Command+Shift+p`-`Python-Select Interpreter`-选择代码目录-选择刚刚创建Python环境目录即可。如果不知道创建的在哪，`poetry shell && which python3`即可。

如涉及cuda的项目，`virtualenvs.create`设置为`false`，poetry环境以conda的为主，一一对应即可。