---
title: How to plot neural network struct
date: 2020-11-19 11:03:15
tags:
  - Neural Network
  - Plot
categories:
  - Plot
---

# PlotNeuralNet Tool
[PlotNeuralNet (GitHub)](https://github.com/HarisIqbal88/PlotNeuralNet "GitHub")
<!--more-->
![FCN-8](PlotNeuralNet.png "FCN-8")

```python
#!/bin/bash


python $1.py 
pdflatex $1.tex

rm *.aux *.log *.vscodeLog
# rm *.tex

if [[ "$OSTYPE" == "darwin"* ]]; then
    open $1.pdf
else
    xdg-open $1.pdf
fi
```
需要在注释掉第8行，这样就可以生成.tex文件和.pdf文件。

建立自己的工程目录和网络结构文件，比如，"myprojects/arch.py"，运行
```python
cd myprojects
bash ../tikzmake.sh arch
```



