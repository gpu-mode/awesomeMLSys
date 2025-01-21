## ML Systems Onboarding Reading List

This is a reading list of papers/videos/repos I've personally found useful as I was ramping up on ML Systems and that I wish more people would just sit and study carefully during their work hours. If you're looking for more recommendations, go through the citations of the below papers and enjoy!

[Conferences](conferences.md) where MLSys papers get published

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
* [Fast Inference from Transformers via Speculative Decoding](https://arxiv.org/abs/2211.17192): This is the paper that helped me grok the difference in performance characteristics between prefill and autoregressive decoding
* [Group Query Attention](https://arxiv.org/pdf/2305.13245): KV caches can be chunky this is how you fix it
* [Orca: A Distributed Serving System for Transformer-Based Generative Models](https://www.usenix.org/conference/osdi22/presentation/yu): introduced continuous batching (great pre-read for the PagedAttention paper).
* [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180): the most crucial optimization for high throughput batch inference
* [Colfax Research Blog](https://research.colfax-intl.com/blog/): Excellent blog if you're interested in learning more about CUTLASS and modern GPU programming
* [Sarathi LLM](https://arxiv.org/abs/2308.16369): Introduces chunked prefill to make workloads more balanced between prefill and decode
* [Epilogue Visitor Tree](https://dl.acm.org/doi/10.1145/3620666.3651369): Fuse custom epilogues by adding more epilogues to the same class (visitor design pattern) and represent the whole epilogue as a tree

## Quantization
* [A White Paper on Neural Network Quantization](https://arxiv.org/abs/2106.08295): Start here this is will give you the foundation to quickly skim all the other papers
* [LLM.int8](https://arxiv.org/abs/2208.07339): All of Dettmers papers are great but this is a natural intro
* [FP8 formats for deep learning](https://arxiv.org/abs/2209.05433): For a first hand look of how new number formats come about
* [Smoothquant](https://arxiv.org/abs/2211.10438): Balancing rounding errors between weights and activations
* [Mixed precision training](https://arxiv.org/abs/1710.03740): The OG paper describing mixed precision training strategies for half

## Long context length
* [RoFormer: Enhanced Transformer with Rotary Position Embedding](https://arxiv.org/abs/2104.09864): The paper that introduced rotary positional embeddings
* [YaRN: Efficient Context Window Extension of Large Language Models](https://arxiv.org/abs/2309.00071): Extend base model context lengths with finetuning
* [Ring Attention with Blockwise Transformers for Near-Infinite Context](https://arxiv.org/abs/2310.01889): Scale to infinite context lengths as long as you can stack more GPUs

## Sparsity
* [Venom](https://arxiv.org/pdf/2310.02065): Vectorized N:M Format for sparse tensor cores when hardware only supports 2:4
* [Megablocks](https://arxiv.org/pdf/2211.15841): Efficient Sparse training with mixture of experts
* [ReLu Strikes Back](https://openreview.net/pdf?id=osoWxY8q2E): Really enjoyed this paper as an example of doing model surgery for more efficient inference

## Distributed
* [Singularity](https://arxiv.org/abs/2202.07848): Shows how to make jobs preemptible, migratable and elastic
* [Local SGD](https://arxiv.org/abs/1805.09767): So hot right now
* [OpenDiloco](https://arxiv.org/abs/2407.07852): Asynchronous training for decentralized training
* [torchtitan](https://arxiv.org/abs/2410.06511): Minimal repository showing how to implement 4D parallelism in pure PyTorch
* [pipedream](https://arxiv.org/abs/1806.03377): The pipeline parallel paper
* [jit checkpointing](https://dl.acm.org/doi/pdf/10.1145/3627703.3650085): a very clever alternative to periodic checkpointing
* [Reducing Activation Recomputation in Large Transformer models](https://arxiv.org/abs/2205.05198): THe paper thatt introduced selective activation checkpointing and goes over activation recomputation strategies
* [Breaking the computation and communication abstraction barrier](https://arxiv.org/abs/2105.05720): God tier paper that goes over research at the intersection of distributed computing and compilers to maximize comms overlap
* [ZeRO: Memory Optimizations Toward Training Trillion Parameter Models](https://arxiv.org/abs/1910.02054): The ZeRO algorithm behind FSDP and DeepSpeed intelligently reducing memory usage for data parallelism.
* [Megatron-LM](https://arxiv.org/abs/1909.08053): For an introduction to Tensor Parallelism
