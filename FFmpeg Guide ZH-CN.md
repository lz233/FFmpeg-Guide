# FFmpeg Guide

## 序言

### 这份指南的由来

我平常总能在群组中看到使用某工厂进行转码的人，这时候我都很想让他们使用 ffmpeg。但是迫于上手繁琐等原因，他们一般都不愿尝试，于是便有了这份指南。

### 这份指南适合谁

这份指南面向有一定命令行基础，想要快速上手，掌握 ffmpeg 基本用法的用户。

对于高级的用法，本指南可能不会有太多叙述。

### 许可

本指南在xxx下进行许可。

## 安装与部署

本节会介绍在大多数常见操作系统上安装与部署 ffmpeg 的方式。在部署完毕后，后续章节会主要在Windows下进行演示。其他平台下的使用方式与在Windows下使用几乎无异。

### Microsoft Windows

#### 获取二进制文件

1. 在[Zeranoe](https://ffmpeg.zeranoe.com/builds/)中选择你需要获取的分支，下载其二进制文件。
2. 转到控制面板-系统和安全-系统-高级系统设置-高级-环境变量，在Path变量中添加 ffmpeg 二进制文件的目录。例如`C:\Users\24843\Documents\exe\ffmpeg`
3. 使用命令提示符/Windows PowerShell/Windows Termainal，键入`ffmpeg`。如果控制台的输出像这样的话，即安装完毕。

`ffmpeg version 4.2 Copyright (c) 2000-2019 the FFmpeg developers`

#### 从源码编译

### Linux

#### 通过命令行部署

#### 获取二进制文件

#### 从源码编译

### Apple Mac OS

#### 通过命令行部署

#### 获取二进制文件

#### 从源码编译

### Apple iOS/iPad OS

#### 从Cydia部署

### Android

#### 从Google Play获取

## 开始工作之前

### 了解当前ffmpeg支持的文件格式与编码器

如果你在桌面操作系统上使用ffmpeg，那么你获取到的一般是最新版本。但如果你在移动平台上使用，则不然，因为这些发行版本一般不由官方维护。因此，你需要检查当前ffmpeg所支持的文件格式与编码器。

### 尝试转换第一个文件

使用ffmpeg进行文件转换很简单，键入以下一行命令就能完成操作。

`ffmpeg -i [input] [ouput]`

在部分系统上，你可以尝试将文件拖入命令行窗口来自动填充命令。

## 转换时可以干的事情

## 小技巧

### ffmpeg还能做更多

除了音视频之外，ffmpeg还能转换图片，并且一般支持ico/webp/png/gif/jpg等多种格式。例如将视频转换为gif：

`
ffmpeg -i input.mp4 output.gif
`