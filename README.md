# CMSR
A novel model for Traffic Video Question Answering

## 1. Project Overview

This repository implements the **CMSR** (Cross‑Modal Stepwise Reasoning) model, a unified framework for **Traffic Video Question Answering (TrafficVQA)** . The model simultaneously addresses two critical limitations in existing methods:
- **Cross‑modal false association** between videos and questions (e.g., spurious co‑occurrence biases).
- **Domain knowledge false association** (irrelevant or noisy knowledge triples interfering with reasoning).

Our solution introduces a **Temporal Consistency Correction Module (TCCM)** and a **Dual Association Denoising Module (DADM)** , followed by a knowledge‑enhanced answer reasoner. Extensive experiments on the SUTD‑TrafficQA benchmark demonstrate state‑of‑the‑art performance across all six subtasks, with superior inference efficiency compared to large video‑language models.

---

## 2. Method Highlights

| Module | Function |
|--------|----------|
| **TCCM** | Uses question‑guided frame filtering and adaptive exponential temporal weighting to suppress isolated false‑association frames, enhancing temporally consistent visual features. |
| **DADM** | Simulates human knowledge retrieval: (i) *scene relevance filtering* selects top‑K knowledge triples related to the video scene; (ii) *semantic consistency verification* further filters triples inconsistent with the current question. |
| **Answer Reasoner** | Employs Transformer‑based cross‑modal fusion and a coarse‑to‑fine contrastive loss with **adaptive weight factors** (μₐ, μₘ) that dynamically balance appearance and motion feature importance. |

The final loss combines a video‑question contrastive term (frame‑level + clip‑level) and an InfoNCE classification loss against candidate answers.
