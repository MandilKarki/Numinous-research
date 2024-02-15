The Evaluations folder contains an array of assessment frameworks and metrics designed for scrutinizing the performance of Large Language Models. It encapsulates tools for both quantitative and qualitative analysis, ensuring comprehensive understanding and validation of LLMs against industry-standard benchmarks in natural language understanding and generation.

Table of Contents -
1) DeepEval
2) 📊  Evals from OpenAI
   

   
Introduction
1) DeepEval - The DeepEval GitHub repository provides an open-source evaluation framework for Large Language Models (LLMs). It's designed for Python and allows users to build and iterate LLM applications efficiently. The repository includes guidelines for setting up the Python environment, installing DeepEval, creating test cases, and custom metrics for evaluating LLM outputs. DeepEval simplifies unit testing of LLM outputs and supports a variety of evaluation metrics and datasets, making it a comprehensive tool for both development and production environments. For more details and usage instructions, you can visit the repository [here](https://github.com/confident-ai/deepeval) .
   Offers 14+ LLM evaluation metrics (both for RAG and fine-tuning use cases), updated with the latest research in the LLM evaluation field. These metrics include:

    G-Eval
    Summarization
    Hallucination
    Faithfulness
    Contextual Relevancy
    Answer Relevancy
    Contextual Recall
    Contextual Precision
    RAGAS
    Bias
    Toxicity
   
    Offers modular components that is extremely simple to plug and use. You can easily mix and match different metrics, or even use DeepEval to build your own evaluation pipeline if needed.
    Treats evaluations as unit tests. With an integration for Pytest, DeepEval is a complete testing suite most developers are familiar with.
    Allows you to generate synthetic datasets using your knowledge base as context, or load datasets from CSVs, JSONs, or Hugging face.
    Offers a hosted platform with a generous free tier to run real-time evaluations in production.


   
3) 📊  Evals from OpenAI: Simplifying and Streamlining LLM Evaluation [link](https://arize.com/blog-course/evals-openai-simplifying-llm-evaluation/#how-to-run-eval)   how to run an evaluation using the oaieval command line interface, the process of building custom evaluations from templates, and creating completion functions for more accurate model responses. The post emphasizes the advantages of using the Eval framework, such as standardized evaluation metrics, ease of use, flexibility, and being open-source.

4) MLFLOW LLM EVALUATE
5) RAGAs - Evaluation framework for your Retrieval Augmented Generation (RAG) pipelines  - RAGAs was build for RAG pipelines. They offer 5 core metrics:

    Faithfulness
    Contextual Relevancy
    Answer Relevancy
    Contextual Recall
    Contextual Precision

These metrics make up the final RAGAs score. DeepEval and RAGAs have very similar implementations, but RAGAs metrics are not self-explaining, making it much harder to debug unsatisfactory results. 






6) Arize AI Phoenix -
Arize AI evaluates LLM applications through extensive observability into LLM traces. However it is extremely limited as it only offers three evaluation criteria:

    QA Correctness
    Hallucination
    Toxicity

7) Truelens -https://github.com/truera/trulens - Evaluation and Tracking for LLM Experiments 
8) Can You Use LLMs as Evaluators? An LLM Evaluation Framework - https://medium.com/@dan_43009/can-you-use-llms-as-evaluators-an-llm-evaluation-framework-8681b400b110
9) Deepchecks - Deepchecks stands out as it is geared more towards evaluating the LLM itself, rather than LLM systems/applications, its open-source offering is unique as it focuses heavily on the dashboards and the visualization UI, which makes it easy for users to visualize evaluation results. https://github.com/deepchecks/deepchecks


Microsoft article - How to Evaluate LLMs: A Complete Metric Framework - https://www.microsoft.com/en-us/research/group/experimentation-platform-exp/articles/how-to-evaluate-llms-a-complete-metric-framework/

Papers
1) Results of WMT23 Metrics Shared  Task: Metrics might be Guilty but References are not Innocent - https://www2.statmt.org/wmt23/pdf/2023.wmt-1.51.pdf
2) https://aclanthology.org/2023.wmt-1.63.pdf - Proceedings of the Eighth Conference on Machine Translation (WMT), pages 756–767
December 6–7, 2023. ©2023 Association for Computational Linguistics
756MetricX-23: The Google Submission to the WMT 2023
Metrics Shared Task
metricsX - https://huggingface.co/google/metricx-23-xxl-v2p0

