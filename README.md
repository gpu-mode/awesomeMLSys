## ML Systems Onboarding Reading List

This is a reading list of papers/videos/repos I've personally found useful as I was ramping up on ML Systems and that I wish more people would just sit and study carefully during their work hours. If you're looking for more recommendations, go through the citations of the below papers and enjoy!


## Attention Mechanism
* [Attention is all you need](https://arxiv.org/abs/1706.03762): Start here, Still one of the best intros
* [Online normalizer calculation for softmax](https://arxiv.org/abs/1805.02867): A must read before reading the flash attention. Will help you get the main "trick" 
* [Self Attention does not need O(n^2) memory](https://arxiv.org/abs/2112.05682): 
* [Flash Attention 2](https://arxiv.org/abs/2307.08691): The diagrams here do a better job of explaining flash attention 1 as well
* [Llama 2 paper](https://arxiv.org/abs/2307.09288): Skim it for the model details
* [gpt-fast](https://github.com/pytorch-labs/gpt-fast): A great repo to come back to for minimal yet performant code
* [Train Short, Test Long: Attention with Linear Biases Enables Input Length Extrapolation](https://arxiv.org/abs/2108.12409): There's tons of papers on long context lengths but I found this to be among the clearest
* Google the different kinds of attention: cosine, dot product, cross, local, sparse, convolutional

## Performance Optimizations
* [Towards Efficient Generative Large Language Model Serving: A Survey from Algorithms to Systems](https://arxiv.org/abs/2312.15234): Wonderful survey, start here
* [Efficiently Scaling transformer inference](https://arxiv.org/abs/2211.05102): Introduced many ideas most notably KV caches
* [Making Deep Learning go Brrr from First Principles](https://horace.io/brrr_intro.html): One of the best intros to fusions and overhead
* [ZeRO: Memory Optimizations Toward Training Trillion Parameter Models](https://arxiv.org/abs/1910.02054): The ZeRO algorithm behind FSDP and DeepSpeed intelligently reducing memory usage for data parallelism.
* [Megatron-LM](https://arxiv.org/abs/1909.08053): For an introduction to Tensor Parallelism
* [Fast Inference from Transformers via Speculative Decoding](https://arxiv.org/abs/2211.17192): This is the paper that helped me grok the difference in performance characteristics between prefill and autoregressive decoding
* [Group Query Attention](https://arxiv.org/pdf/2305.13245): KV caches can be chunky this is how you fix it
* [Orca: A Distributed Serving System for Transformer-Based Generative Models](https://www.usenix.org/conference/osdi22/presentation/yu): introduced continuous batching (great pre-read for the PagedAttention paper).
* [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180): the most crucial optimization for high throughput batch inference

## Quantization
* [A White Paper on Neural Network Quantization](https://arxiv.org/abs/2106.08295): Start here this is will give you the foundation to quickly skim all the other papers
* [LLM.int8](https://arxiv.org/abs/2208.07339): All of Dettmers papers are great but this is a natural intro
* [FP8 formats for deep learning](https://arxiv.org/abs/2209.05433): For a first hand look of how new number formats come about
* [Smoothquant](https://arxiv.org/abs/2211.10438): Balancing rounding errors between weights and activations#

## Long context length
* [RoFormer: Enhanced Transformer with Rotary Position Embedding](https://arxiv.org/abs/2104.09864): The paper that introduced rotary positional embeddings
* [YaRN: Efficient Context Window Extension of Large Language Models](https://arxiv.org/abs/2309.00071): Extend base model context lengths with finetuning
* [Ring Attention with Blockwise Transformers for Near-Infinite Context](https://arxiv.org/abs/2310.01889): Scale to infinite context lengths as long as you can stack more GPUs

## Sparsity
* [Venom](https://arxiv.org/pdf/2310.02065): Vectorized N:M Format for sparse tensor cores
* [Megablocks](https://arxiv.org/pdf/2211.15841): Efficient Sparse training with mixture of experts
* [ReLu Strikes Back](https://openreview.net/pdf?id=osoWxY8q2E): Activation sparsity in LLMs
* [Sparse Llama](https://arxiv.org/pdf/2405.03594)
* [Simple pruning for LLMs](https://arxiv.org/pdf/2306.11695) 
