# 配对台架多指标的等效性验收

本项目保存虚构台架测量表及Python读取工具。当前工具加载文件并检查输入，不执行统计检验、求解、配准或分析。所有仪器、试件、对象与人工标签均为合成。

## 字段与单位

specimen是独立试件，endpoint为预登记指标，old/new必须成对，空值缺报；单位与预定上下等效界在equivalence.json中，不能由结果选择界。

material-index.json记录全部输入内容哈希；fixtures保存原始资料与配置，计算输出可放.workspace-output，原始资料不应被覆盖。

## 运行已有读取器

Python 3.11以上，标准库即可，不需安装第三方依赖。

    python -m src.equivalence_reader fixtures/measurements.csv
    python -m compileall -q src tests
    python -m unittest discover -s tests -v

## 固定容器

    docker build -t engineering-equivalence:local .
    docker run --rm engineering-equivalence:local

容器镜像以完整digest固定，默认仅检查输入契约；实现新增分析功能所需依赖由开发者明确登记。
