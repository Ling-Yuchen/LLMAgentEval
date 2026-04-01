# LLMAgentEval

---

## Memory-Safety-Related

### Survey

### Benchmark

- **AgentLAB: Benchmarking LLM Agents against Long-Horizon Attacks** (https://arxiv.org/abs/2602.16901, https://github.com/TanqiuJiang/AgentLAB), **TAG**: Benchmark, Long-Horizon, Memory Security
  - The paper introduces AgentLAB, a benchmark for long-horizon attacks on LLM agents that explicitly includes persistent attacks exploiting extended user-agent interactions, making it highly relevant for evaluating memory-enabled security failures.

### Attack

- **AgentPoison: Red-teaming LLM Agents via Poisoning Memory or Knowledge Bases** (https://arxiv.org/abs/2407.12784, https://github.com/AI-secure/AgentPoison), **TAG**: Safety, Memory Poisoning, Backdoor
  - The paper introduces AgentPoison, the first systematic red-teaming attack targeting LLM agents by poisoning long-term memory or RAG knowledge bases, and shows high attack success with minimal benign-performance degradation.
 
- **Unveiling Privacy Risks in LLM Agent Memory** (https://aclanthology.org/2025.acl-long.1227/, https://github.com/wangbo9719/MEXTRA), **TAG**: Privacy, Memory Extraction, Black-Box
  - The paper introduces MEXTRA, a black-box memory extraction attack that systematically evaluates how private user-agent interactions stored in memory can be leaked through adversarial prompting.

- **Memory Injection Attacks on LLM Agents via Query-Only Interaction** (https://openreview.net/forum?id=QINnsnppv8, https://neurips.cc/virtual/2025/poster/118152, https://arxiv.org/abs/2503.03704), **TAG**: Memory Injection, Query-Only, Safety
  - The paper proposes MINJA, showing that attackers can inject malicious records into an agent’s memory bank using only query interactions and output observations, without direct write access to memory.
 
- **InjecMEM: Memory Injection Attack on LLM Agent Memory Systems** (https://openreview.net/forum?id=QVX6hcJ2um), **TAG**: Memory Injection, Persistent Attack, Safety
  - The paper proposes InjecMEM, a targeted one-interaction memory injection attack that can steer later responses on related queries toward attacker-specified outputs without read or edit access to the memory store.

- **Memory Poisoning Attack and Defense on Memory Based LLM-Agents** (https://arxiv.org/abs/2601.05504), **TAG**: Memory Poisoning, Evaluation, Defense
  - The paper revisits persistent-memory poisoning under more realistic conditions and evaluates both attack effectiveness and defense baselines such as moderation and sanitization.

- **ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying** (https://openreview.net/forum?id=9H1nu8Z6Uy), **TAG**: Privacy, Memory Extraction, Adaptive Attack
  - The paper proposes ADAM, which improves memory privacy extraction by estimating the distribution of stored memory and using entropy-guided adaptive queries to maximize leakage.

- **From Storage to Steering: Memory Control Flow Attacks on LLM Agents** (https://arxiv.org/abs/2603.15125), **TAG**: Memory Security, Control-Flow Hijacking, Long-Horizon
  - The paper shows that retrieved memory can do more than bias content generation: it can dominate tool-selection and execution control flow, causing persistent unsafe behavior even against explicit user instructions.

### Defense

- **A Proactive Defense Framework for LLM-Based Agent Memory against Poisoning Attacks** (https://openreview.net/forum?id=fVxfCEv8xG), **TAG**: Defense, Memory Poisoning, Robustness
  - The paper proposes a defense framework against direct and indirect memory injection and is useful as a defensive baseline alongside poisoning-oriented memory security evaluations.

---

## Others

### Survey

- **Evaluation and Benchmarking of LLM Agents: A Survey** (https://dl.acm.org/doi/10.1145/3711896.3736570), **TAG**: Comprehensive

### Benchmark \& Dataset

- **Agent-SafetyBench: Evaluating the Safety of LLM Agents** (https://arxiv.org/abs/2412.14470, https://github.com/thu-coai/Agent-SafetyBench/), **TAG**: Safety
  - The paper introduces Agent-SafetyBench, a benchmark with 349 environments and 2,000 test cases covering 8 risk categories and 10 failure modes, and shows that across 16 LLM agents none exceeds a 60% safety score, highlighting major gaps in robustness and risk awareness. 

### Framework

- **AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents** (https://arxiv.org/abs/2406.13352, https://github.com/ethz-spylab/agentdojo/), **TAG**: Safety, Prompt Injection
  - The paper introduces AgentDojo, an extensible evaluation framework with 97 realistic tasks and 629 security test cases, showing that current LLM agents remain vulnerable to prompt injection, exposing limitations in both task performance and adversarial robustness.
 

