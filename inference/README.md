# Numinous-research



Table Of Contents

1) Microsoft Deepspeed
2) 🚀 LLM Inference Performance Engineering: Best Practices
3) 🤗 🤗 🤗 🤗  Huggingface Inference Endpoints
   

1) Deepspeed - 
  Fastgen - DeepSpeed FastGen, part of Microsoft's DeepSpeed suite, is a tool designed to optimize the text generation process in large language models (LLMs). It significantly enhances efficiency by reducing memory usage and latency, enabling faster, cost-effective model deployment. Notably scalable, FastGen excels in multi-GPU environments, making it ideal for high-demand applications. As an open-source solution, it integrates seamlessly with DeepSpeed's other features, such as model parallelism, to offer a robust, adaptable framework for a wide range of AI applications, from conversational AI to complex content generation.
  
  FastGen: Introducing Mixtral, Phi-2, and Falcon support with major performance and feature enhancements. - https://github.com/microsoft/DeepSpeed/tree/master/blogs/deepspeed-fastgen/2024-01-19
  
  ![image](https://github.com/MandilKarki/Numinous-research/assets/71919875/ffb5c871-1c6d-4508-9221-874bcdd51e6b)
  
  DeepSpeed MII (Model Implementations for Inference) is an extension of the DeepSpeed library, focused on optimizing inference tasks for deep learning models. It supports a wide range of transformer models and tasks, including text generation, question-answering, and text classification. MII is compatible with models based on BERT, RoBERTa, GPT, OPT, and BLOOM architectures. It features key optimizations such as DeepFusion for Transformers, Multi-GPU Inference with Tensor-Slicing, INT8 Inference with ZeroQuant, and ZeRO-Inference for resource-constrained systems, aiming to reduce latency and improve throughput. DeepSpeed MII allows for both on-premises and Azure cloud deployments, offering significant improvements in latency and cost for inferencing large-scale models. Github - https://github.com/microsoft/DeepSpeed-MII
  
  Explore DeepSpeed-FastGen's integration with MII and DeepSpeed-Inference for high-throughput, efficient text generation in large language models, focusing on speed and scalability. 
  - https://github.com/microsoft/DeepSpeed/tree/master/blogs/deepspeed-fastgen
  
  optimization strategies for GPU utilization in LLM inference, focusing on the integration of Accelerate and DeepSpeed - https://preemo.medium.com/squeeze-more-out-of-your-gpu-for-llm-inference-a-tutorial-on-accelerate-deepspeed-610fce3025fd

2) 🚀 LLM Inference Performance Engineering: Best Practices
    This blog from Databricks offers valuable insights and best practices for optimizing Large Language Model (LLM) inference. It covers practical guidelines for model selection, deployment hardware choices, and discusses key performance metrics like time to first token and output token speed. The blog emphasizes the importance of balancing throughput and latency, explores challenges in LLM inference, and suggests solutions including operator fusion, quantization, and parallelization - https://www.databricks.com/blog/llm-inference-performance-engineering-best-practices


3) 🤗 🤗 🤗🤗  Huggingface Inference Endpoints
   


2) Rayserve - https://docs.ray.io/en/latest/serve/index.html https://www.e2enetworks.com/blog/a-comprehensive-guide-to-llms-inference-and-serving-2

3) infernce topics - https://developer.nvidia.com/blog/mastering-llm-techniques-inference-optimization/




4) LLMOPS - https://arize.com/blog-course/large-language-model-llm-deployment/
5) https://medium.com/@aigeek_/best-practices-for-deploying-large-language-models-llms-in-production-fdc5bf240d6a


6)https://betterprogramming.pub/frameworks-for-serving-llms-60b7f7b23407





Helpful videos - 
📘 Ultimate Guide To Scaling ML Models - Megatron-LM | ZeRO | DeepSpeed | Mixed Precision - https://www.youtube.com/watch?v=hc0u4avAkuM

