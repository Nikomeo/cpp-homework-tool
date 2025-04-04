# cpp-homework-tool

这是一套专为SJTU-程序设计原理与方法（2025春）设计的作业自动评判与打包工具，主要目的是省去广大学生每次测试代码都需要写一堆命令行的困扰。包含两个主要组件，详情在TL;DR后面。

## 0. TL;DR

### a. 不报错的前提条件

1. 两个程序必须与`assignment`或`challenge`文件夹放在同一目录下
2. 文件夹名称必须是assignmentx或challengex，其中x为正整数
3. assignment或challenge文件夹下必须有作业题目的子文件夹，比如1_xxx
4. 确保你的主文件名称永远是main.cpp

### b. 功能介绍

1. `auto_judger.py`可以自动判题并反馈测试具体结果（依赖于judger.py，judger_batch.py与data文件夹等 ，所以别删掉原文件。但是，随机添加文件是可以的。）
2. `auto_package.py`可以一键打包并打开提交作业的网页。目前可以做到收集所有.cpp和.h文件，所以不要在题目文件夹下保留其他cpp文件。zip文件会保存在**assignmentx文件夹里面**。

## 1. 自动评判工具 (auto_judger.py)

此工具用于自动检查你的代码能否过关，可以:

- 自动定位最新的assignment文件夹
- 检查单个题目的正确性
- 一键检查所有题目
- 显示详细的评判结果
- 在测试案例未通过时显示标准输入、标准输出、用户输出

### 使用方法
```
python auto_judger.py
```
或直接双击运行。按照提示输入题目序号，或输入'a'检查所有题目。

## 2. 作业打包工具 (auto_package.py)

此工具用于打包你的作业文件以便提交，可以:

- 自动定位最新的assignment文件夹
- 自动从子文件夹收集所有.cpp和.h文件
- 按照规定格式生成zip压缩包，保存在assignmentx文件夹里面
- 保存学号信息，避免重复输入
- 打包完成后可一键打开交作业网站

### 使用方法
```
python auto_package.py
```
或直接双击运行。按照提示确认学号，然后等待打包完成。

## 文件结构

```
.
├── auto_judger.py      # 自动评判工具
├── auto_package.py     # 作业打包工具
├── student_config.txt  # 存储学号信息(会自动生成)
├── assignment1/        # 作业文件夹
│   ├── judger_batch.py # 判题程序
│   ├── 1_xxx/          # 题目1文件夹
│   │   ├── main.cpp    # 源代码
│   │   └── ...
│   ├── 2_yyy/          # 题目2文件夹
│   └── ...
└── ...
```

## 注意事项

1. **两个程序必须与assignment文件夹放在同一目录下**
2. 打包工具只会收集符合"x_yyy"格式文件夹中的.cpp和.h文件
3. 评判工具需要原始assignment文件夹中的judger_batch.py才能工作
4. 首次使用需要输入12位学号，之后会自动保存

## 作者

李效成-主要代码编写
史浩廷-代码优化与提升
肖壤-拓展功能编写
