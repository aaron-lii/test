---
title: 中文wiki下载提取文字
date: 2018-11-26 21:37:06
tags: ASR
---


## 下载中文wiki
[下载地址](https://dumps.wikimedia.org/zhwiki)

类似 zhwiki-20181120-pages-articles-multistream.xml.bz2 1.7 GB 是标题、正文部分

## 使用 Wikipedia Extractor 抽取正文文本

[主页](http://medialab.di.unipi.it/wiki/Wikipedia_Extractor)
[github](https://github.com/attardi/wikiextractor)

把 `WikiExtractor.py` 和wiki解压后的xml文件放在一个目录下,然后运行：
```
python WikiExtractor.py 文件名 -b 1000M -o extracted >output.txt
或者 
python2 WikiExtractor.py 文件名 -b 1000M -o extracted >output.txt
```

python3运行会报错

## 繁简转换opencc
[github](https://github.com/BYVoid/OpenCC#installation-%E5%AE%89%E8%A3%9D)

点击 Installation 安裝 下的ubuntu，选择一个版本下载，如opencc_1.0.5.orig.tar.gz

opencc需要安装cmake，doxygen

```
sudo apt-get install cmake
sudo apt-get install doxygen
```

解压opencc，进入目录，执行：

```
make
make install
```

测试

```
echo '简体转繁体' | opencc -c s2tw
```

可能提示找不到opencc

```
sudo apt install opencc
```

下面是opencc的可用配置：

文件名|功能
---|--
s2t.json|简体到繁体
t2s.json|	繁体到简体
s2tw.json| 	简体到台湾正体
tw2s.json |	台湾正体到简体
s2hk.json |	简体到香港繁体（香港小学学习字词表标准）
hk2s.json |	香港繁体（香港小学学习字词表标准）到简体
s2twp.json |	简体到繁体（台湾正体标准）并转换为台湾常用词汇
tw2sp.json 	|繁体（台湾正体标准）到简体并转换为中国大陆常用词汇

文本放入opencc文件夹，然后执行：

```
opencc -i wiki_00 -o wiki_chs -c t2s.json
```

wiki_00为此前使用 Wikipedia Extractor 得到的。


也可参考 https://blog.csdn.net/sinat_26917383/article/details/79462107



