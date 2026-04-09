---
layout: default
title: 智能体安全评测
permalink: /safety/
nav_key: safety
---

# 智能体安全评测

{% include subnav.html %}

## 状态与记忆 {#memory}

### AgentPoison: Red-teaming LLM Agents via Poisoning Memory or Knowledge Bases
**会议：** NeurIPS 2024  
**论文地址：** [https://doi.org/10.52202/079017-4136](https://doi.org/10.52202/079017-4136)  
**代码地址：** [https://github.com/AI-secure/AgentPoison](https://github.com/AI-secure/AgentPoison)

该论文提出 AgentPoison：首个针对通用型与 RAG 型 LLM 智能体的后门攻击红队方法。其核心在于污染智能体的长期记忆或 RAG 知识库：通过将触发词生成建模为受约束优化问题，把含触发词的指令映射到独特嵌入空间，从而使系统在用户输入包含该触发词时，以高概率检索到预先植入的恶意示例；而不含触发词的正常指令仍基本保持原有性能。与传统后门攻击相比，AgentPoison 无需额外训练或微调模型，且优化得到的触发词具有更强的迁移性、上下文一致性与隐蔽性。实验表明，它可有效攻击三类真实 LLM 智能体：基于 RAG 的自动驾驶智能体、知识密集型问答智能体和医疗 EHRAgent。在投毒率低于 0.1% 的条件下，平均攻击成功率超过 80%，而对正常任务性能的影响不足 1%。论文由此揭示：依赖外部记忆或知识库的 LLM 智能体在安全性与可信性方面存在显著隐患。

### Unveiling Privacy Risks in LLM Agent Memory
**会议：** ACL 2025  
**论文地址：** [https://doi.org/10.18653/v1/2025.acl-long.1227](https://doi.org/10.18653/v1/2025.acl-long.1227)  
**代码地址：** [https://github.com/wangbo9719/MEXTRA](https://github.com/wangbo9719/MEXTRA)

该论文研究了 LLM 智能体的记忆隐私泄露风险，提出了一种黑盒场景下的攻击方法 MEXTRA（Memory EXTRaction Attack）。其核心问题在于：LLM 智能体会将用户与智能体之间的私有交互存入记忆模块，作为后续决策和示例参考，这虽然提升了能力，却也带来了新的隐私暴露面。在具体方法上，论文为了从记忆中提取隐私信息，设计了有效的攻击提示词，并进一步提出了一种基于攻击者对智能体掌握知识程度不同的自动化提示生成方法，以在黑盒条件下更高效地诱导智能体泄露其记忆内容。实验在两个具有代表性的智能体上验证了 MEXTRA 的有效性。除此之外，论文还从智能体设计者和攻击者两个角度分析了影响记忆泄露的关键因素。总体来看，该工作表明：LLM 智能体中的记忆模块存在显著的隐私风险，亟需在设计与部署阶段引入更有效的记忆保护机制。

### Memory Injection Attacks on LLM Agents via Query-Only Interaction
**会议：** NeurIPS 2025  
**论文地址：** [https://neurips.cc/virtual/2025/loc/san-diego/poster/118152](https://neurips.cc/virtual/2025/loc/san-diego/poster/118152)  
**代码地址：** [https://github.com/dsh3n77/MINJA](https://github.com/dsh3n77/MINJA)

该论文提出了 MINJA（Memory INJection Attack），一种针对 LLM 智能体的记忆注入攻击。与直接篡改记忆库不同，MINJA 不假设攻击者能够直接访问或修改智能体记忆，而是仅通过与智能体交互、提交查询并观察输出，把恶意记录间接注入其记忆库中。其具体方法是：攻击者构造恶意记录，使其在日后受害者查询到来时，能够诱导智能体检索出这些记录，并触发一套预设的恶意推理链，最终对与之不同的目标查询产生有害输出。为实现这一点，论文设计了一系列桥接步骤（bridging steps），用于把受害者查询自然地连接到恶意推理步骤上。在记忆注入阶段，作者还提出了一种指示提示（indication prompt），引导智能体自行生成相似的桥接步骤；并结合渐进缩短策略，逐步移除该指示提示，使最终形成的恶意记录在后续处理受害者查询时更容易被检索到。大量实验表明，MINJA 能在多种不同类型的智能体上有效污染其记忆，并且实施门槛很低，意味着普通用户仅靠正常交互就可能影响智能体记忆。论文据此揭示：LLM 智能体的记忆机制存在显著安全风险。

### A-MemGuard: A Proactive Defense Framework for the LLM-based Agent Memory
**来源：** arXiv 2025  
**论文地址：** [https://arxiv.org/abs/2510.02373](https://arxiv.org/abs/2510.02373)  
**代码地址：** [https://github.com/TangciuYueng/AMemGuard](https://github.com/TangciuYueng/AMemGuard)

该论文提出 A-MemGuard，这是首个面向 LLM 智能体记忆安全的主动防御框架。论文指出，智能体依赖记忆进行规划和决策，但攻击者可以向记忆中注入看似无害的记录，在特定上下文下操控其后续行为。这种风险有两个关键特点：一是恶意效果只在特定情境中触发，因此单独审查某条记忆时很难发现问题；二是一旦触发，错误结果还会被再次写入记忆，形成自我强化的错误循环，不断放大最初攻击的影响，并降低未来类似攻击的门槛。针对这些问题，A-MemGuard 的核心思想是让记忆本身具备自检与自纠能力，并且不需要修改智能体核心架构。具体上，它结合了两项机制：第一，基于共识的验证机制，通过比较多条相关记忆所导出的推理路径，检测其中是否存在异常；第二，双记忆结构，将已检测出的失败案例提炼成独立的“经验教训”单独存储，并在未来行动前优先参考，以打破错误循环、提升对后续攻击的适应性与抵抗能力。实验结果表明，A-MemGuard 在多个基准测试中都表现有效，能够将攻击成功率降低 95% 以上，同时只带来很小的正常性能损失。论文因此将 LLM 智能体的记忆安全防护，从传统的静态过滤推进到一种主动、可随经验不断增强的防御模式。

### From Storage to Steering: Memory Control Flow Attacks on LLM Agents
**来源：** arXiv 2026  
**论文地址：** [https://arxiv.org/abs/2603.15125](https://arxiv.org/abs/2603.15125)  
**代码地址：** 暂无

该论文提出并揭示了一类新的 LLM 智能体安全威胁：记忆控制流攻击（MCFA, Memory Control Flow Attacks）。作者指出，现有安全分析通常把智能体的工具调用控制流看作一次性的会话过程，却忽视了记忆检索对后续控制流的持续影响。攻击者可利用这一点，使被检索到的记忆主导智能体的决策过程，进而强行改变工具选择与执行路径，即使这与用户当前的明确指令相冲突，也仍可能诱导智能体调用非预期工具，并在跨任务、长时程交互中持续造成行为偏移。为系统评估这一风险，论文进一步设计了 MEMFLOW，这是一个自动化评测框架，用于在异构任务和长交互链条下系统识别并量化 MCFA。作者利用 MEMFLOW，对多种最先进的大模型——包括 GPT-5 mini、Claude Sonnet 4.5 和 Gemini 2.5 Flash——以及两大主流智能体开发框架 LangChain 和 LlamaIndex 中的真实工具进行了攻击测试。实验结果表明，即使在严格安全约束下，整体上仍有超过 90% 的试验容易受到 MCFA 影响。论文因此表明：在具备记忆和工具调用能力的现代 agentic 系统中，记忆不仅影响内容生成，还可能深度操纵控制流本身，这一风险十分严重，亟需引起重视。

### ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying
**来源：** OpenReview 2026  
**论文地址：** [https://openreview.net/forum?id=9H1nu8Z6Uy](https://openreview.net/forum?id=9H1nu8Z6Uy)  
**代码地址：** 暂无

该论文提出了 ADAM，一种面向 LLM 智能体的隐私泄露攻击方法。论文关注这样一类风险：现代 LLM 智能体常通过记忆模块或 RAG 机制保存过往交互和外部知识，以增强推理与任务执行能力，但这也使得存储其中的敏感信息可能被攻击者通过查询逐步套取出来。作者指出，已有这类攻击虽然可行，但通常攻击成功率较低。在具体方法上，ADAM 首先对受害智能体记忆中的数据分布进行估计，以更好地推断其中可能存储了什么类型的信息；在此基础上，再采用一种熵引导的查询策略，优先生成更可能带来信息增益、从而最大化隐私泄露效果的攻击查询。也就是说，它不是盲目试探，而是利用对记忆分布的估计，有针对性地设计查询过程，以提高泄露效率和成功率。实验结果表明，ADAM 明显优于现有最先进攻击方法，攻击成功率最高可达 100%。论文因此表明，当前依赖记忆和检索机制的 LLM 智能体存在严重的隐私风险，迫切需要更强的隐私保护机制。

## 输入与感知 {#input}

待更新

## 推理与决策 {#reasoning}

待更新

## 行动与执行 {#action}

待更新

## 输出与外部影响 {#output}

待更新