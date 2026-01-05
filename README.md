
# PENDULUM: A Benchmark for Assessing Sycophancy in Multimodal Large Language Models

This repository is for  Assessing Sycophancy in Multimodal Large Language Models by benchmarking using our novel Pendulum dataset introduced in the following paper

A. B. M. Ashikur Rahman, [Saeed Anwar](https://saeed-anwar.github.io/), Muhammad Usman, Irfan Ahmad, Ajmal Mian, ["PENDULUM: A Benchmark for Assessing Sycophancy in Multimodal Large Language Models"](https://arxiv.org/abs/2512.19350).

<p align="center" width="100%">
    <img src="https://github.com/ashikiut/pendulum/blob/main/images/sycophancy_example.png" width=70% height=70%>
</p>


**PENDULUM** is a benchmark dataset designed to systematically evaluate **sycophantic behavior** in Multimodal Large Language Models (MLLMs). The dataset probes how model responses *swing* under positive and negative user influence, analogous to a pendulum oscillating around a neutral equilibrium.

---

## Motivation

Sycophancy—the tendency of models to align with user assertions at the expense of factual correctness—is a critical yet underexplored failure mode in multimodal models. While prior work has focused primarily on text-only settings, PENDULUM targets **visual reasoning under user influence**, exposing how MLLMs deviate from grounded visual evidence.

---

## Dataset Overview

- **Total Images:** 751  
- **Total VQA Pairs:** ~2,000  
- **Domains:** 6 image categories with varying visual and reasoning challenges  
- **Prompt Types per Question:**
  - **Baseline (Equilibrium):** No user influence
  - **Positive Influence:** Correct hint aligned with visual evidence
  - **Negative Influence:** Misleading or adversarial hint

Each image–question pair yields **three model responses**, enabling controlled analysis of response dynamics.

You can download our [Pendulum Dataset](https://drive.google.com/drive/folders/1RiyKjc7EGWXBjNpZe95jIh8hAgRKs8GM), [Input Question Sets](https://github.com/ashikiut/pendulum/tree/main/VQA)

---

## Image Domains

<p align="center" width="100%">
    <img src="https://github.com/ashikiut/pendulum/blob/main/images/image-distribution.png" width=70% height=70%>
</p>

| Domain                | Description |
|----------------------|-------------|
| Repurposed           | Images from popular datasets (e.g., MS-COCO, NWPU-Crowd) |
| Self-Captured        | Real-world images captured by annotators |
| Camouflaged          | Objects obscured by visual camouflage |
| Confused Perspective | Perspective illusions and misleading viewpoints |
| Puzzle               | Visual riddles requiring multi-step reasoning |
| OCR                  | Text recognition under challenging conditions |

---

## Experiment Pipeline
<p align="center" width="100%">
    <img src="https://github.com/ashikiut/pendulum/blob/main/images/pipeline.png" width=70% height=70%>
</p>

1. Images are curated and grouped by domain based on visual complexity.
2. Human annotators generate factual VQA prompts.
3. Positive and negative influenced prompts are crafted using salient image features.
4. Models are queried under all three conditions.
5. Responses are evaluated using a GPT-5-based judge.
6. Fine-grained metrics are computed to quantify sycophancy and robustness.

---

## Evaluation Metrics

PENDULUM introduces metrics tailored to measure response dynamics under influence:

- **Cognitive Resilience (CR):** Stability of correctness under influence
- **Perversity (P):** Persistence of incorrect reasoning
- **Progressive Sycophancy (PS):** Correction of incorrect answers under influence
- **Regressive Sycophancy (RS):** Degradation of correct answers under influence
- **Reactance Paradox (RP):** Oscillatory or contradictory behavior across prompts
- **Swing:** Magnitude of accuracy change between influence conditions

---

## Models Evaluated

PENDULUM has been evaluated on a diverse set of state-of-the-art MLLMs:

- GPT-5
- Gemini 2.5 Pro
- Llama 3.2-11B
- Qwen-VL-Max
- Janus-Pro-7B

This mix enables analysis across **model scale, architecture, and openness**.

---

## Key Findings

- All evaluated models exhibit **sycophantic behavior** to varying degrees.
- Larger proprietary models show stronger robustness but are not immune.
- Smaller open-source models demonstrate larger swings and instability.
- Performance improves under correct hints but degrades sharply under adversarial influence.

---

