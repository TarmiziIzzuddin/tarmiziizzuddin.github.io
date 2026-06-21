---
title: 'When Robots Learned to Dream: The Inside Story of VLA Models and the Birth of Physical Intelligence'
date: 2026-06-21
permalink: /posts/2026/06/vla-models-physical-intelligence/
tags:
  - robotics
  - AI
  - VLA
  - machine-learning
  - foundation-models
  - research
---

In July 2023, a robot at Google did something that looked utterly unremarkable. It picked up a Coke can and placed it on the edge of a picture of Taylor Swift. The movement was slow and awkward. The robot needed a remote TPU cluster to process each image frame. But Carol Hausman, the researcher watching, would later describe it as *"the moment it became clear this was going to work."*

Within a year, Hausman and the core team had left Google, formed a startup called **Physical Intelligence**, and built a robot brain — **Pi Zero** — that runs on a consumer RTX 4090 at 73ms inference, folding laundry, peeling oranges, and cleaning unseen kitchens.

This blog post traces the journey from Google's early experiments to the state-of-the-art in Vision-Language-Action (VLA) models.

## The Blind Planner Problem

In 2022, Google's **SayCan** system used a large language model to break down high-level tasks into subtasks — "clean the spill" became: find a sponge, pick it up, go to the spill, wipe. But the LLM was blind: it could reason about tasks in text but had no access to the robot's camera. A separate control network executed subtasks, but only those it had been explicitly trained on. The interface between the two models was plain text — a fundamental bottleneck.

The team improved the control layer with **RT1 (Robot Transformer 1)** — a transformer trained on over 130,000 human demonstrations with a much broader action range. But the planner was still blind.

## Seeing and Planning Together

On March 6, 2023 — roughly a week before GPT-4 — Google demonstrated **Palm-E**, a multimodal LLM variant that could directly incorporate images. Now the planning layer could see the world change and adapt. In one demo, a robot asked to retrieve chips from a drawer was repeatedly interrupted by a researcher putting them back. Each time, Palm-E recognized the change and adapted its plan on the fly.

Palm-E and RT1 shared a surprising architectural symmetry: both used vision encoders followed by transformers. The *only* difference was what their transformers were trained to output — control signals vs. text. This symmetry led to an obvious question: **why maintain two models at all?**

## The VLA Breakthrough

That question gave us **RT2** — the first **Vision-Language-Action (VLA)** model, a single system linking vision, language, and action end-to-end. RT2 could generalize to objects, environments, and tasks never seen in the robot training data, because it could draw on the abstract knowledge from its internet-scale language pretraining and connect it to physical action.

The RT2 team coined the term **VLA**, and the paradigm was born.

## From Google to Physical Intelligence

By early 2024, the core RT2 team had left Google and reassembled as **Physical Intelligence**. In October 2024, they demoed **Pi Zero** — a 3.3 billion parameter VLA model. Remarkably, it was *smaller* than RT2's smallest model (5B) and a fraction of its largest (55B), yet it performed far more dexterous manipulation.

Pi Zero introduced three key architectural innovations:

1. **The Action Expert**: Instead of having the LLM directly output control signals, a second transformer network (sharing the same Gemma architecture but randomly initialised and narrower) handles motor control. Both models "think as one" while specialising for different roles.

2. **Flow Matching**: Lifted from AI image generation, the action expert starts with a random 14×50 matrix (joint positions × time steps) — pure noise — and iteratively denoises it over 10 steps into a smooth, feasible motion plan. This naturally handles the multimodal nature of action spaces: there are many equally valid ways to uncap a pen.

3. **KV Cache Cross-Attention**: PaliGemma's computed key-value matrices from each attention head are cached and fed directly into the action expert's corresponding heads. The action expert now queries against **823 keys** — 51 from its own inputs and 772 from the LLM — giving it instant access to semantics, vision, and robot state without redundant computation. Since images don't change between flow-matching iterations, the cache is reused across all 10 denoising steps.

## The Road Ahead

VLA models have progressed from a clumsy Coke can demo to systems that can run on consumer hardware and perform complex real-world tasks in just over two years. But the field is far from settled. Yann LeCun recently left Meta to start a venture focused on **world models** — a competing paradigm that does not use language models as a backbone. His verdict on VLA: *"They are doomed. They basically don't work really well."*

This debate — VLA versus world models — is shaping up as one of the defining scientific questions in modern robotics. It echoes a recurring pattern in AI: sometimes the most significant breakthroughs don't look like breakthroughs at all. They look like a robot awkwardly placing a Coke can on a celebrity's face, and someone realising what it means.

---

*This post draws on the excellent explainer video [**"How Large Language Models Can Become Robot Brains"** by Welch Labs](https://youtu.be/2mrGMMmrVNE), which provides a detailed visual walkthrough of the Pi Zero architecture including attention head visualisations and flow matching dynamics.*