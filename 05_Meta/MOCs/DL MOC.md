---
type: moc
created: 2026-05-02
tags:
  - moc
---

# DL MOC

> **What this MOC covers:** Deep learning fundamentals through modern transformer architectures — the conceptual progression from neural networks to LLMs.

## 🌐 Overview
Deep Learning is my primary technical learning track alongside FAANG prep. This MOC covers the conceptual progression from neural networks through transformers, including modern variants (BERT, GPT). Goal: research-paper fluency and the ability to reason about modern LLM architectures from first principles. Current depth: foundational; building.

## 📖 Synthesis Notes
- [[From Neural Networks to Transformers]]

## 🛤️ Learning Path: From Neural Networks to Transformers

### 1. Foundations: Neural Networks
- [ ] [[Backpropagation computes gradients via reverse-mode autodiff]]
- [ ] [[Activation functions introduce non-linearity into neural networks]]
- [ ] [[Universal approximation theorem and what it does and doesn't promise]]

### 2. Sequence Models: RNNs
- [ ] [[RNNs encode sequence order through sequential hidden state]]
- [ ] [[Vanilla RNNs suffer from vanishing gradients on long sequences]]

### 3. Gated Architectures: LSTM & GRU
- [ ] [[LSTM gates solve vanishing gradients via additive memory cell]]
- [ ] [[GRU simplifies LSTM by merging cell and hidden state]]

### 4. Encoder-Decoder & Attention
- [ ] [[Encoder-decoder architecture compresses input then generates output]]
- [ ] [[Bahdanau attention lets decoder look back at all encoder states]]

### 5. The Transformer
- [ ] [[Self-attention is permutation-equivariant without positional encoding]]
- [ ] [[Multi-head attention captures different representation subspaces]]
- [ ] [[Transformers replace recurrence with parallel attention computation]]

### 6. Modern Variants
- [ ] [[BERT uses only the encoder for bidirectional representations]]
- [ ] [[GPT uses only the decoder for autoregressive generation]]

## 🔬 Sub-Topics
<!-- Atomic notes that don't fit the linear path. Promote a section to its own MOC when it grows past ~15 items. -->

### Optimization

### Regularization

### Architecture Search


## 📚 Resources
<!-- Auto-fetched: every literature note tagged with [[DL MOC]] appears here -->
```dataview
LIST FROM "03_Resources" 
WHERE contains(MOCs, this.file.link) AND type = "literature"
SORT file.ctime DESC
```

### Books
- 

## 🛤️ Related Roadmaps
- [[ML Roadmap]]

## ❓ Open Questions
<!-- Things I don't yet understand. Convert to atomic notes once resolved. -->
- 

## 🔗 Related MOCs
- [[ML MOC]]

## 🗂️ All Notes in This MOC
<!-- Auto-fetched: complete inventory of everything tagged with [[DL MOC]] -->
```dataview
LIST FROM "" 
WHERE contains(MOCs, this.file.link) AND file.name != this.file.name
SORT file.mtime DESC
```