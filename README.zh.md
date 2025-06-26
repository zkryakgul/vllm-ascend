<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/vllm-project/vllm-ascend/main/docs/source/logos/vllm-ascend-logo-text-dark.png">
    <img alt="vllm-ascend" src="https://raw.githubusercontent.com/vllm-project/vllm-ascend/main/docs/source/logos/vllm-ascend-logo-text-light.png" width=55%>
  </picture>
</p>

<h3 align="center">
vLLM Ascend Plugin
</h3>

<p align="center">
| <a href="https://www.hiascend.com/en/"><b>关于昇腾</b></a> | <a href="https://vllm-ascend.readthedocs.io/en/latest/"><b>官方文档</b></a> | <a href="https://slack.vllm.ai"><b>#sig-ascend</b></a> | <a href="https://discuss.vllm.ai/c/hardware-support/vllm-ascend-support"><b>用户论坛</b></a> | <a href="https://tinyurl.com/vllm-ascend-meeting"><b>社区例会</b></a> |
</p>

<p align="center">
<a href="README.md"><b>English</b></a> | <a><b>中文</b></a>
</p>

---
*最新消息* 🔥

- [2025/03] 我们和vLLM团队举办了[vLLM Beijing Meetup](https://mp.weixin.qq.com/s/CGDuMoB301Uytnrkc2oyjg)! 你可以在[这里](https://drive.google.com/drive/folders/1Pid6NSFLU43DZRi0EaTcPgXsAzDvbBqF)找到演讲材料.
- [2025/02] vLLM社区正式创建了[vllm-project/vllm-ascend](https://github.com/vllm-project/vllm-ascend)仓库，让vLLM可以无缝运行在Ascend NPU。
- [2024/12] 我们正在与 vLLM 社区合作，以支持 [[RFC]: Hardware pluggable](https://github.com/vllm-project/vllm/issues/11162).
---
## 总览

vLLM 昇腾插件 (`vllm-ascend`) 是一个由社区维护的让vLLM在Ascend NPU无缝运行的后端插件。

此插件是 vLLM 社区中支持昇腾后端的推荐方式。它遵循[[RFC]: Hardware pluggable](https://github.com/vllm-project/vllm/issues/11162)所述原则：通过解耦的方式提供了vLLM对Ascend NPU的支持。

使用 vLLM 昇腾插件，可以让类Transformer、混合专家(MOE)、嵌入、多模态等流行的大语言模型在 Ascend NPU 上无缝运行。

## 准备

- 硬件：Atlas 800I A2 Inference系列、Atlas A2 Training系列
- 操作系统：Linux
- 软件：
  * Python >= 3.9, < 3.12
  * CANN >= 8.1.RC1
  * PyTorch >= 2.5.1, torch-npu >= 2.5.1.post1.dev20250619
  * vLLM (与vllm-ascend版本一致)

## 开始使用

请查看[快速开始](https://vllm-ascend.readthedocs.io/en/latest/quick_start.html)和[安装指南](https://vllm-ascend.readthedocs.io/en/latest/installation.html)了解更多.

## 贡献
请参考 [CONTRIBUTING]((https://vllm-ascend.readthedocs.io/en/latest/developer_guide/contribution/index.html)) 文档了解更多关于开发环境搭建、功能测试以及 PR 提交规范的信息。

我们欢迎并重视任何形式的贡献与合作：
- 请通过[Issue](https://github.com/vllm-project/vllm-ascend/issues)来告知我们您遇到的任何Bug。
- 请通过[用户论坛](https://discuss.vllm.ai/c/hardware-support/vllm-ascend-support)来交流使用问题和寻求帮助。

## 分支策略
vllm-ascend有主干分支和开发分支。

- **main**: 主干分支，与vLLM的主干分支对应，并通过昇腾CI持续进行质量看护。
- **vX.Y.Z-dev**: 开发分支，随vLLM部分新版本发布而创建，比如`v0.7.3-dev`是vllm-asend针对vLLM `v0.7.3`版本的开发分支。

下面是维护中的分支：

| 分支         | 状态         | 备注                  |
|------------|------------|---------------------|
| main       | Maintained | 基于vLLM main分支CI看护   |
| v0.7.1-dev | Unmaintained | 只允许文档修复 |
| v0.7.3-dev | Maintained | 基于vLLM v0.7.3版本CI看护 |

请参阅[版本策略](https://vllm-ascend.readthedocs.io/en/latest/community/versioning_policy.html)了解更多详细信息。

## 社区例会

- vLLM Ascend 每周社区例会: https://tinyurl.com/vllm-ascend-meeting
- 每周三下午，15:00 - 16:00 (UTC+8, [查看您的时区](https://dateful.com/convert/gmt8?t=15))

## 许可证
Apache 许可证 2.0，如 [LICENSE](./LICENSE) 文件中所示。
