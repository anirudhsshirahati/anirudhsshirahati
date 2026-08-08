+++
title = "Projects"
slug = "projects"
description = "Selected AI engineering work, from local model inference to deployed LLM products."
+++

Two projects that represent the work I care about most: taking language models out of the notebook and into software that people can actually use.

## Inkwell: LLM Powered Document Automation

<span class="project-meta">Python · Hugging Face Transformers · Llama 3.1 · OpenCV · Pydantic · Gradio · GCP</span>

Inkwell turns a plain English instruction into accurately positioned data on a scanned, non-interactive PDF form. The hard part is that these documents have no form fields at all. They are flat images of paper.

To solve that, I built a computer vision pipeline using OpenCV morphological analysis that detects and recovers 227 addressable cells from a flat scan, reconstructing the structure a fillable form would have had. Inference runs locally on Meta Llama 3.1 8B Instruct through Hugging Face Transformers, quantized to 4-bit NF4 with bitsandbytes so the whole thing fits in roughly 5.6 GB of VRAM.

Because a language model writing into a legal or medical form cannot be allowed to improvise, generation is constrained by JSON Schema and validated with Pydantic, with automated correction when the model returns something invalid. Automated verification tests confirm document integrity by checking that protected regions remain pixel identical to the source.

The architecture is deliberately privacy focused. There are no external API calls, so sensitive documents never leave the local execution environment.

<span class="project-status">Private repository</span>

## PreLegal: AI Powered Legal Document Drafting

<span class="project-meta">Python · FastAPI · Next.js · Claude · OpenRouter · Docker · GitHub Actions</span>

A full-stack SaaS platform that drafts professional legal agreements through conversation. You describe what you need in plain English, the AI asks the questions a lawyer would ask, and a clean document builds as you go.

The conversational layer gathers requirements, generates structured document content and produces a customized agreement, supporting 11 document types based on Common Paper open standards. Claude, accessed through OpenRouter, is the drafting engine.

Behind it is a FastAPI backend handling user authentication, document persistence and PDF generation, with automated CI/CD workflows in GitHub Actions deploying to Render.

<span class="project-links">[GitHub](https://github.com/anirudhsshirahati/prelegal) · [Live App](https://prelegal-t4hf.onrender.com)</span>

If you have questions or want to explore a collaboration, reach out via my **[Contact](/contact)** page.
