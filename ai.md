# AI
> Thoughts and references related to AI.

## Learning
- [NanoChat](https://github.com/karpathy/nanochat/tree/master): ChatGPT trained fromm scratch.
- [Smol Training Playbook](https://huggingface.co/spaces/HuggingFaceTB/smol-training-playbook)
  - [FineWeb](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1): Building datasets at scale.
  - [Ultra Scale Playbook](https://huggingface.co/spaces/nanotron/ultrascale-playbook): Orchestrating GPUs for a training run
  - [Evaluation Guidebook](https://github.com/huggingface/evaluation-guidebook): Choose the right evaluations

## Coding agents
- [Goose](https://github.com/block/goose)
- [Factory](https://factory.ai/)

## Projects
- [KumoRFM](https://github.com/kumo-ai/kumo-rfm): A foundation model for business data. Predictions over structured data.
- [Liquid Nanos](https://www.liquid.ai/blog/introducing-liquid-nanos-frontier-grade-performance-on-everyday-devices): Frontier-grade performance on small models.
  - [LFM-1B-Math](https://www.liquid.ai/research/lfm-1b-math-can-small-models-be-concise-reasoners): Detailed description of how it was installed.
  - [HF models](https://huggingface.co/collections/LiquidAI/liquid-nanos-68b98d898414dd94d4d5f99a)
- [TOON](https://github.com/johannschopplich/toon): Text object-oriented notation to save tokens when interacting with LLMs
- [NoF1.ai](https://nof1.ai/): Model crypto trading agents and portfolio comparison.

## Bookmarks
- [RAG search and GraphRAG for financial data](https://substack.com/home/post/p-150951876)
- [LM Arena Leaderboard](https://lmarena.ai/leaderboard/text)

## Papers 
- [Agentic context engineering](https://www.arxiv.org/pdf/2510.04618)
- [Less is more: Recursive reasoning with tiny networks](https://arxiv.org/pdf/2510.04871v1)

## Trends
> High-level trends and ideas

- Environments are a key asset to train AIs through RL. The closer the training environment is to the real one, the better it will end up operating. In the coming years I expect the programming of RL environments for AI to be as important as wiring the agents themselves (esp. for robotics and real world --analogous and flawed environments--). See [prime intellect's](https://www.primeintellect.ai/) RL environments as the seed for this trend.
- Small language models outperform LLMs for agentic behavior: 
  - See paper: https://arxiv.org/pdf/2510.03847
