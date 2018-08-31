# Vim 插件开发指南

## 简介

Vim 插件开发者无疑是从 Vim 的用户转换而来，而在开发 Vim 插件之前，你需要掌握 Vim 的基本使用技巧，可以先阅读 《Vim 从入门到精通》，该文章主要介绍了 Vim 的基本使用技巧。

开发 Vim 插件，离不开 Vim 脚本语言，需要对 Vim 脚本语言有一个大致的了解。《Vim 脚本语法指南》讲解了 Vim 脚本的一些语法技巧。

此外，在开发 Vim 插件之前，你还需要了解 vimrc 和 Vim 插件的区别。

## Vim 插件的项目结构

在开发 Vim 插件之前，需要了解一下，一个 Vim 插件项目的目录结构是怎样的，以及每一个目录里文件的意义是什么。 Vim 插件标准的目录结构为：

```text
autoload/               自动载入脚本
plugin/                 在 Vim 启动时将被载入的脚本
ftdetect/               文件类型识别脚本
```

下面，我们来逐一说明下每一个目录的用途：

**autoload/** 

顾名思义，该文件夹下的脚本会在特点条件下自动被载入。这里的特定条件指的是当某一个 autoload 类型的函数被调用，并且 Vim 当前环境下并未定义该函数时。
比如调用 `call helloworld#init()` 时，Vim 会先检测当前环境下是否定义了该函数，若没有，则在 `autoload/` 目录下找 `helloworld.vim` 这一文件，
并将其载入，载入完成后执行 `call helloworld#init()`.
