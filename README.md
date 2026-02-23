一、PAT 安装
1.1 工具简介
Process Analysis Toolkit (PAT) 是一款面向流程建模、仿真与优化的形式化验证工具。它支持多种建模和分析技术，广泛应用于生产过程设计、服务系统优化、供应链分析及业务流程改进等领域。PAT 提供丰富的模型库、优化工具和数据分析功能，帮助用户快速构建精确的流程模型，并通过仿真与优化实现业务目标。

1.2 系统要求
操作系统：Windows 10 及以上版本（推荐）
硬件要求：建议 4GB 以上内存，1GHz 以上处理器

1.3 下载与安装
访问 PAT 官方网站下载页面：
https://pat.comp.nus.edu.sg/?page_id=2660
选择对应操作系统版本的安装包进行下载。
运行下载的安装程序，按照提示完成安装。

二、mCRL2 安装

2.1 工具简介
mCRL2 是一个用于分析并发系统行为的形式化验证工具集，支持进程代数建模、模型检测和性能分析等功能。

2.2 下载与安装
访问 mCRL2 官方下载页面：
https://www.mcrl2.org/web/user_manual/download.html
根据操作系统选择对应版本（Windows、Linux 或 macOS）。
下载安装包后，按照安装向导完成安装。

三、Python 环境配置
3.1 Python 简介
Python 是一种广泛使用的高级编程语言，在形式化验证、数据分析、自动化脚本等领域具有丰富的生态支持。

3.2 下载与安装
访问 Python 官方网站：
https://www.python.org/downloads/
选择适合您操作系统的 Python 版本（建议 Python 3.8 或更高版本）。
运行安装程序，务必勾选“Add Python to PATH”（将 Python 添加到系统环境变量），然后点击“Install Now”。

三、实验步骤

1.1、实验条件需求
硬件：计算机一台（建议选择Windows 10及以上系统）；
软件：已安装PAT、mCRL2、python。

1.2、实验步骤

编码为CSP#，30个案例的代码在ECA文件中
使用PAT工具中的“simulation”进行系统的仿真，点击“Process”并选择“System”后点击“Generate Graph”生成的状态空间。

将缓冲区大小为1-10的异步组合仿真后生成的状态空间图依次导出，导出文件为txt格式，点击“Expor”导出txt文件。

在Python中将txt文件转换成.mcrl2文件。

运行mCRL2后找到转换后的.mcrl2文件的保存路径。

右击缓冲区大小为1的异步组合的.mcrl2文件，并依次点击“Transformation”、“mcrl22lps”。点击“Run”生成对应的.lps文件。

右击缓冲区大小为1的异步组合的.lps文件，并依次点击“Transformation”、“lps2lts”。点击“Run”生成对应的.lts文件。

继续生成缓冲区大小为2-10的异步组合的.lts文件。

右击缓冲区大小为2的异步组合的.lts文件，并依次点击“Analysis”、“Itscompare”。

选择“Weak-Bisimulation”后点击“Browse”。找到缓冲区大小为1异步组合的.lts文件的保存路径并点击“打开”。

点击“Run”对缓冲区大小为2的异步组合和缓冲区大小为1的异步组合进行等价检测。

所示结果为“false”，则表明缓冲区大小为2的异步组合和缓冲区大小为1的异步组合不等价，需要继续比较缓冲区大小为k和k+1的异步组合直到等价检测结果为“true”时终止。若k≥10，则方法不确定性终止，系统稳定值未知。
