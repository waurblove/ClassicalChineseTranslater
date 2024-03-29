# ClassicalChineseTranslater
<div align="center">
  <img src="https://github.com/InternLM/lmdeploy/assets/36994684/0cf8d00f-e86b-40ba-9b54-dc8f1bc6c8d8" width="600"/>
  <br /><br />

![GitHub Repo stars](https://img.shields.io/github/stars/LZHgrla/xtuner-template?style=social)
![license](https://img.shields.io/github/license/LZHgrla/xtuner-template.svg)
[![issue resolution](https://img.shields.io/github/issues-closed-raw/LZHgrla/xtuner-template)](https://github.com/LZHgrla/xtuner-template/issues)
[![open issues](https://img.shields.io/github/issues-raw/LZHgrla/xtuner-template)](https://github.com/LZHgrla/xtuner-template/issues)

👋 加入我们：[![Static Badge](https://img.shields.io/badge/-grey?style=social&logo=wechat&label=WeChat)](https://cdn.vansin.top/LZHgrla/xtuner.jpg)
[![Static Badge](https://img.shields.io/badge/-grey?style=social&logo=twitter&label=Twitter)](https://twitter.com/intern_lm)
[![Static Badge](https://img.shields.io/badge/-grey?style=social&logo=discord&label=Discord)](https://discord.gg/xa29JuW87d)

🔍 探索我们的模型：
[![Static Badge](https://img.shields.io/badge/-gery?style=social&label=🤗%20Huggingface)](https://huggingface.co/xtuner)
[![Static Badge](https://img.shields.io/badge/-gery?style=social&label=🤖%20ModelScope)](https://www.modelscope.cn/organization/xtuner)


</div>



## 介绍

XTuner-Template 是一个模版仓库，提供了一个使用 [XTuner](https://github.com/InternLM/xtuner) 工具库训练大模型的“起点”。

除了支持模版仓库的基础功能，其也集成了一系列 Git / GitHub 的自动化功能：

- 提交前检查（[Pre-commit](./.pre-commit-config.yaml) check）
- GitHub 自动化工作流（[Workflows](./.github/workflows) of [GitHub Actions](https://github.com/InternLM/xtuner-template/actions)）
- [Issue 模版](./.github/ISSUE_TEMPLATE)、[Pull request (PR) 模版](.github/pull_request_template.md)



### 安装

1. 准备 Python 虚拟环境：

   ```bash
   conda create --name xtuner-env python=3.10 -y
   conda activate xtuner-env
   ```

2. 克隆该仓库：

   ```shell
   git clone https://github.com/waurblove/ClassicalChineseTranslater.git
   cd ./ClassicalChineseTranslater
   ```

3. 安装依赖库：

   ```shell
   pip install -r requirements.txt
   ```

### 训练

1. 开始

   ```shell
   # On a single GPU
   xtuner train ${YOUR_CONFIG} --deepspeed deepspeed_zero2
   ```

   - `--deepspeed` 表示使用 [DeepSpeed](https://github.com/microsoft/DeepSpeed) 🚀 来优化训练过程。XTuner 内置了多种策略，包括 ZeRO-1、ZeRO-2、ZeRO-3 等。如果用户期望关闭此功能，请直接移除此参数。

2. 将保存的 `.pth` 模型（如果使用的DeepSpeed，则将会是一个文件夹）转换为 HuggingFace 模型：

   ```shell
   xtuner convert pth_to_hf ${YOUR_CONFIG} ${PTH} ${SAVE_PATH}
   ```

### 对话

```shell
xtuner chat ${NAME_OR_PATH_TO_LLM} [optional arguments]
```

可选参数：

- `--adapter`: 指定 adapter 名字或路径。
- `--prompt-template`: 指定对话模版（应与所对话的 LLM 对齐）。
- `--system`: 指定对话的系统字段。
- `--bits {4,8,None}`: 指定 LLM 的比特数。默认为 fp16。
- `--no-streamer`: 是否移除 streamer。
- 更多信息，请执行 `xtuner chat -h` 查看。

## 数据集出处
https://github.com/scagin/cctc

## 开源许可证

该项目采用 [Apache License 2.0 开源许可证](LICENSE)。

