# BrainAI | NeuroMaster

## Table of Contents

<!-- toc -->
- [Docs](https://www.brainco-hz.com/docs/NeuroMaster)
- [Arduino IDE Setup](<https://www.brainco-hz.com/docs/NeuroMaster/docs/BrianAI_Arduino-C.docx>)
  <!-- ATmega328 -->
- [主控与编程板通信协议](https://brainco.yuque.com/qc91eq/lbx4ww/kngkgigdgbgghw3s)

- [慧编程下载](https://mblock.makeblock.com/zh/download/)
- [慧编程扩展](https://ext.makeblock.com/)
- [慧编程文档-添加扩展](https://www.yuque.com/makeblock-help-center-zh/mblock-5/device-library-and-extension-center)

- [General](#general)
  - [Arduino library Registry](<https://github.com/arduino/library-registry>)
  - [Arduino Style Guide](<https://docs.arduino.cc/learn/contributions/arduino-library-style-guide>)
  - [Arduino Lint](<https://arduino.github.io/arduino-lint>)
  - [How is the Library Manager index generated?](#how-is-the-library-manager-index-generated)

- [Lint](#lint)  

<!-- tocstop -->

## General

### How is the Library Manager index generated?

[The Library Manager index](http://downloads.arduino.cc/libraries/library_index.json) contains the data for every release of every one of the thousands of libraries that have been added to the Library Manager list. This index is used by Library Manager to provide installation and updates of the libraries as well as to generate automated documentation pages for the [Arduino Library Reference](https://www.arduino.cc/reference/en/libraries/).

Every hour, the automated Library Manager indexer system:

1. checks every repository in the Library Manager list for new tags, updating [the logs](https://github.com/arduino/library-registry/blob/main/FAQ.md#can-i-check-on-library-releases-being-added-to-library-manager) accordingly
1. checks whether those tags meet [the requirements for addition to the index](https://github.com/arduino/library-registry/blob/main/FAQ.md#update-requirements)
1. adds entries to the index for compliant tags
1. pushes the updated index to Arduino's download server

## Lint

```sh
sudo curl -fsSL https://raw.githubusercontent.com/arduino/arduino-lint/main/etc/install.sh | BINDIR=~/local/bin sh
export PATH=$PATH:~/local/bin
arduino-lint --recursive --library-manager submit

arduino-lint --compliance strict
arduino-cli lib search NeuroMaster
https://downloads.arduino.cc/libraries/logs/github.com/arduino-libraries/Servo/
https://downloads.arduino.cc/libraries/logs/github.com/BrainCoTech/brain_arduino/

# Update
https://github.com/BrainCoTech/brain_arduino/
arduino-lint --recursive --library-manager update
git tag v0.0.7  # 使用新的版本号创建标签
git push origin v0.0.7  # 推送标签到远程仓库
```
