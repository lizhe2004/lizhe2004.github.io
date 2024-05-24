---
title: 大模型应用效果评估工具介绍和对比
toc: true
date: 2024-05-01
tags: [大模型,检索增强生成]
categories: [人工智能]
description: 大模型应用效果评估工具介绍和对比
banner: 
cover: 
author: 李大侠
breadcrumb: true
leftbar:
  - recent
  - related
  - tagcloud
rightbar:
  - ghuser
  - toc
---

lamaIndex is a development framework for Large Language Model (LLM) applications. It is widely used by developers to create Retrieval-Augmented Generation (RAG) applications. During the development process of RAG applications, it’s crucial to evaluate related data to better tune and optimize the applications. As RAG technology advances, more effective evaluation tools have emerged to facilitate accurate and efficient evaluation of RAG applications. In this article, we’ll introduce some RAG evaluation tools that can be integrated with LlamaIndex and compare them.
LlamaIndex 是大型语言模型（LLM）应用程序的开发框架。它被开发人员广泛用于创建检索增强生成（RAG）应用程序。在 RAG 应用程序的开发过程中，评估相关数据以更好地调整和优化应用程序至关重要。随着 RAG 技术的发展，出现了更多有效的评估工具，以帮助准确、高效地评估 RAG 应用程序。本文将介绍一些可与 LlamaIndex 集成的 RAG 评估工具，并对它们进行比较。

What Are RAG Evaluation Tools?
什么是 RAG 评估工具？
RAG evaluation tools are methods or frameworks used to test and evaluate text generation systems based on retrieval. They assess accuracy, content quality, and relevance, among other metrics. They are valuable in helping developers understand and optimize RAG applications for real-world use. Compared to manual evaluation, RAG evaluation tools are more objective, accurate, and efficient, allowing for large-scale evaluations through automation. Some applications even integrate these tools into CI/CD processes to achieve automated evaluation and optimization.
RAG 评估工具是用于测试和评估基于检索的文本生成系统的方法或框架。它们评估准确性、内容质量和相关性等指标。它们在帮助开发人员了解和优化 RAG 应用程序以适应实际使用方面非常有价值。与人工评估相比，RAG 评估工具更加客观、准确和高效，可以通过自动化进行大规模评估。有些应用程序甚至将这些工具集成到 CI/CD 流程中，以实现自动评估和优化。

Entity Terms 实体术语
RAG applications typically use specific terms for evaluation. These terms may vary among different evaluation tools. Here are the common entity definitions:
RAG 应用程序通常使用特定的评估术语。这些术语在不同的评估工具中可能会有所不同。以下是常见的实体定义：

Question: Refers to the user’s query. In some tools, it’s also called Input or Query.
问题：指用户的询问。在某些工具中，它也被称为 Input 或 Query 。
Context: Refers to the retrieved document context. Some tools call it Retrieval Context.
上下文：指检索到的文档上下文。有些工具称之为 Retrieval Context 。
Answer: Refers to the generated answer. Different terms like Actual Output or Response may be used.
答案：指生成的答案。可使用 Actual Output 或 Response 等不同术语。
Ground Truth: Refers to manually labeled correct answers. It is used to evaluate the accuracy of generated answers.
地面实况：指人工标注的正确答案。它用于评估生成答案的准确性。
We will use these terms consistently in the following tool descriptions to maintain clarity and facilitate comparison.
在以下工具说明中，我们将统一使用这些术语，以保持清晰并便于比较。

Preparations 准备工作
Test Documents 测试文件
We use content from the Marvel movie “Avengers” as test documents. This data is primarily from the Wikipedia entry on Avengers, containing plot information from four Avengers movies.
我们使用漫威电影《复仇者联盟》中的内容作为测试文档。这些数据主要来自维基百科的复仇者联盟词条，其中包含四部复仇者联盟电影的情节信息。

Datasets 数据集
Based on the test documents, we create a dataset containing Question and Ground Truth. Here's the defined dataset:
根据测试文档，我们创建了一个包含 Question 和 Ground Truth 的数据集。 以下是已定义的数据集：

questions = [
    "What mysterious object did Loki use in his attempt to conquer Earth?",
    "Which two members of the Avengers created Ultron?",
    "How did Thanos achieve his plan of exterminating half of all life in the universe?",
    "What method did the Avengers use to reverse Thanos' actions?",
    "Which member of the Avengers sacrificed themselves to defeat Thanos?",
]

ground_truth = [
    "The Tesseract",
    "Tony Stark (Iron Man) and Bruce Banner (The Hulk).",
    "By using the six Infinity Stones",
    "By collecting the stones through time travel.",
    "Tony Stark (Iron Man)",
]
Retrieval Engine 检索引擎
Next, we’ll use LlamaIndex to create a standard RAG retrieval engine. The evaluation tools will use this engine to generate Answer and Context:
接下来，我们将使用 LlamaIndex 创建一个标准的 RAG 检索引擎。评估工具将使用该引擎生成 Answer 和 Context ：

from llama_index.core import VectorStoreIndex, SimpleDirectoryReader

documents = SimpleDirectoryReader("./data").load_data()
vector_index = VectorStoreIndex.from_documents(documents)
query_engine = vector_index.as_query_engine(similarity_top_k=2)
We load documents from the data directory.
我们从 data 目录中加载文件。
Create a document vector index with VectorStoreIndex.
用 VectorStoreIndex 创建文件矢量索引。
Convert the document vector index to a query engine and set the similarity threshold to 2.
将文档向量索引转换为查询引擎，并将相似性阈值设为 2。
TruLens 透镜
TruLens is a software tool designed to evaluate and improve LLM applications.
TruLens 是一种软件工具，旨在评估和改进 LLM 应用程序。


Image source: https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
图片来源：https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
Evaluation Metrics 评估指标
TruLens primarily uses the following metrics to evaluate RAG applications:
TruLens 主要使用以下指标来评估 RAG 应用程序：

Answer Relevance: Assesses how well the Answer responds to the Question, ensuring helpfulness and relevance.
答案相关性：评估 Answer 对 Question 的回应程度，确保其有用性和相关性。
Context Relevance: Evaluate the relevance of the Context to the Question, providing the basis for LLM answers.
语境相关性：评估 Context 与 Question 的相关性，为 LLM 答案提供依据。
Groundedness: Examines whether the Answer aligns with the facts presented in the Context.
基础性：审查 Answer 是否与 Context 中陈述的事实一致。
Ground Truth: Compares the Answer with manually labeled Ground Truth to ensure accuracy.
地面实况：将 Answer 与人工标注的 Ground Truth 进行比较，以确保准确性。
Usage Example 使用示例
Here’s a code snippet demonstrating how to use TruLens for RAG evaluation:
下面的代码片段演示了如何使用 TruLens 进行 RAG 评估：

import numpy as np
from trulens_eval import Tru, Feedback, TruLlama
from trulens_eval.feedback.provider.openai import OpenAI
from trulens_eval.feedback import Groundedness, GroundTruthAgreement

openai = OpenAI()
golden_set = [{"query": q, "response": r} for q, r in zip(questions, ground_truth)]
ground_truth = Feedback(
    GroundTruthAgreement(golden_set).agreement_measure, name="Ground Truth"
).on_input_output()
grounded = Groundedness(groundedness_provider=openai)
groundedness = (
    Feedback(grounded.groundedness_measure_with_cot_reasons, name="Groundedness")
    .on(TruLlama.select_source_nodes().node.text)
    .on_output()
    .aggregate(grounded.grounded_statements_aggregator)
)
qa_relevance = Feedback(
    openai.relevance_with_cot_reasons, name="Answer Relevance"
).on_input_output()
qs_relevance = (
    Feedback(openai.qs_relevance_with_cot_reasons, name="Context Relevance")
    .on_input()
    .on(TruLlama.select_source_nodes().node.text)
    .aggregate(np.mean)
)
tru_query_engine_recorder = TruLlama(
    query_engine,
    app_id="Avengers_App",
    feedbacks=[
        ground_truth,
        groundedness,
        qa_relevance,
        qs_relevance,
    ],
)
with tru_query_engine_recorder as recording:
    for question in questions:
        query_engine.query(question)
tru = Tru()
tru.run_dashboard()
This code snippet uses TruLens to evaluate RAG applications. It defines feedback metrics like Ground Truth, Groundedness, Answer Relevance, and Context Relevance. It then records the query engine's results with TruLlama, and runs the evaluation with Tru to display the results.
此代码片段使用 TruLens 评估 RAG 应用程序。它定义了 Ground Truth 、 Groundedness 、 Answer Relevance 和 Context Relevance 等反馈指标，然后用 TruLlama 记录查询引擎的结果，并用 Tru 运行评估以显示结果。

Evaluation Results 评估结果
TruLens’s evaluation results can be viewed through a local service accessed via a browser. The evaluation results include overall scores and detailed metrics. The reasons behind the scores are also visible. Below is an example of TruLens’s evaluation results:
TruLens 的评估结果可通过浏览器访问本地服务查看。评估结果包括总分和详细指标。分数背后的原因也清晰可见。以下是 TruLens 评估结果的示例：


Previously, I’ve written an article on TruLens, which provides a more detailed description and usage examples.
此前，我写过一篇关于 TruLens 的文章，其中提供了更详细的说明和使用示例。

Ragas 喇叭
Ragas is another framework for evaluating RAG applications. Compared to TruLens, Ragas offers more detailed metrics.
Ragas 是另一个评估 RAG 应用程序的框架。与 TruLens 相比，Ragas 提供了更详细的指标。


Image source: https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
图片来源：https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
Evaluation Metrics 评估指标
Ragas uses the following metrics to evaluate RAG applications:
Ragas 采用以下指标来评估 RAG 申请：

Faithfulness: Evaluate the consistency between the Question and Context.
忠实性：评估 Question 和 Context 之间的一致性。
Answer Relevance: Assesses the consistency between the Answer and Question.
答案相关性：评估 Answer 和 Question 之间的一致性。
Context Precision: Checks whether Ground Truth ranks high in Context.
上下文精度：检查 Ground Truth 在 Context 中的排名是否靠前。
Context Recall: Evaluate the consistency between Ground Truth and Context.
背景回忆：评估 Ground Truth 和 Context 之间的一致性。
Context Entities Recall: Assesses the consistency between entities in Ground Truth and Context.
上下文实体回忆：评估 Ground Truth 和 Context 中实体的一致性。
Context Relevancy: Evaluate the consistency between Question and Context.
上下文相关性：评估 Question 和 Context 之间的一致性。
Answer Semantic Similarity: Assesses the semantic similarity between Answer and Ground Truth.
答案语义相似性：评估 Answer 和 Ground Truth 之间的语义相似性。
Answer Correctness: Evaluate the correctness of Answer relative to Ground Truth.
答案正确性：评估 Answer 相对于 Ground Truth 的正确性。
Aspect Critique: Includes evaluations of other aspects, like harmfulness, correctness, etc.
方面批评：包括对其他方面的评价，如有害性、正确性等。
Usage Example 使用示例
The official Ragas documentation provides an example of integrating with LlamaIndex, but the code is outdated. Here’s an updated example:
Ragas 官方文档提供了一个与 LlamaIndex 集成的示例，但代码已经过时。以下是更新后的示例：

from ragas.metrics import (
    faithfulness,
    answer_relevancy,
    context_relevancy,
    answer_correctness,
)
from ragas import evaluate
from datasets import Dataset

metrics = [
    faithfulness,
    answer_relevancy,
    context_relevancy,
    answer_correctness,
]
answers = []
contexts = []
for q in questions:
    response = query_engine.query(q)
    answers.append(response.response)
    contexts.append([sn.get_content() for sn in response.source_nodes])
data = {
    "question": questions,
    "contexts": contexts,
    "answer": answers,
    "ground_truth": ground_truth,
}
dataset = Dataset.from_dict(data)
result = evaluate(dataset, metrics)
result.to_pandas().to_csv("output/ragas-evaluate.csv", sep=",")
In this example, we: 在这个例子中，我们

Use questions and ground_truth for the input data.
输入数据使用 questions 和 ground_truth 。
Employ metrics similar to those used in TruLens.
采用与 TruLens 类似的指标。
Manually construct the dataset, adding questions, answers, and contexts.
手动构建数据集，添加问题、答案和上下文。
Save the evaluation results to a local file.
将评估结果保存到本地文件。
Evaluation Results 评估结果
Ragas’s evaluation results can be viewed in local files. The results contain scores for each evaluation metric. Below is an example of Ragas’s evaluation results:
Ragas 的评估结果可在本地文件中查看。评估结果包含每个评估指标的得分。下面是 Ragas 评估结果的示例：


The evaluation results from Ragas and TruLens show quite a difference, especially in the Context Relevancy metric, where the scores are notably lower. In fact, when evaluating Context, Ragas recommends using Context Precision and Context Recall as the primary metrics. However, for comparison with TruLens, we used Context Relevancy.
Ragas 和 TruLens 的评估结果显示出相当大的差异，尤其是在 Context Relevancy 指标上，得分明显较低。事实上，在评估 Context 时，Ragas 建议使用 Context Precision 和 Context Recall 作为主要指标。不过，为了与 TruLens 进行比较，我们使用了 Context Relevancy 。

In Ragas's evaluation results, we only see the scores without any explanation for the reasons behind the scores.
在 Ragas 的评估结果中，我们只看到了分数，却没有解释分数背后的原因。

DeepEval 深度评估
DeepEval is an open-source evaluation framework for LLMs that allows for evaluation tasks to be run like unit tests.
DeepEval 是用于 LLMs 的开源评估框架，可像单元测试一样运行评估任务。


Image source: https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
图片来源：https://www.trulens.org/trulens_eval/core_concepts_rag_triad/
Evaluation Metrics 评估指标
DeepEval uses the following evaluation metrics, with some designed for RAG applications and others for other LLM uses:
DeepEval 使用以下评估指标，其中一些指标专为 RAG 应用而设计，其他指标则用于其他 LLM 用途：

Faithfulness: Evaluates consistency between Question and Context.
忠实性评估 Question 和 Context 之间的一致性。
Answer Relevance: Assesses consistency between Answer and Question.
答案相关性：评估 Answer 和 Question 之间的一致性。
Contextual Precision: Checks whether Ground Truth ranks high in Context.
上下文精度：检查 Ground Truth 在 Context 中的排名是否靠前。
Contextual Recall: Evaluates consistency between Ground Truth and Context.
上下文回忆：评估 Ground Truth 和 Context 之间的一致性。
Contextual Relevancy: Evaluates consistency between Question and Context.
上下文相关性：评估 Question 和 Context 之间的一致性。
Hallucination: Measures the degree of hallucinations.
幻觉：测量幻觉的程度。
Bias: Evaluates bias levels.
偏差：评估偏差水平。
Toxicity: Measures the presence of toxicity, including personal attacks, sarcasm, or threats.
毒性：衡量是否存在毒性，包括人身攻击、讽刺或威胁。
Ragas: Allows for using Ragas for evaluation and generating explanations.
拉格允许使用 Ragas 进行评估和生成解释。
Knowledge Retention: Evaluates the persistence of information.
知识保留：评估信息的持久性。
Summarization: Evaluate the effectiveness of summarization.
总结：评估总结的有效性。
G-Eval: G-Eval is a framework for performing evaluation tasks using a Large Language Model (LLM) with a Chain of Thought (CoT). It can evaluate LLM outputs based on any custom criteria. For more information, check out this paper.
G-Eval：G-Eval 是一个使用大型语言模型（LLM）和思维链（CoT）执行评估任务的框架。它可以根据任何自定义标准对 LLM 输出进行评估。更多信息，请查看本文。
Usage Example 使用示例
DeepEval can run evaluation tasks like unit tests. Here is a simple example:
DeepEval 可以像单元测试一样运行评估任务。下面是一个简单的例子：

import pytest
from deepeval.metrics import (
    AnswerRelevancyMetric,
    FaithfulnessMetric,
    ContextualRelevancyMetric,
)
from deepeval.test_case import LLMTestCase
from deepeval import assert_test
from deepeval.dataset import EvaluationDataset

def generate_dataset():
    test_cases = []
    for i in range(len(questions)):
        response = query_engine.query(questions[i])
        test_case = LLMTestCase(
            input=questions[i],
            actual_output=response.response,
            retrieval_context=[node.get_content() for node in response.source_nodes],
            expected_output=ground_truth[i],
        )
        test_cases.append(test_case)
    return EvaluationDataset(test_cases=test_cases)

dataset = generate_dataset()

@pytest.mark.parametrize(
    "test_case",
    dataset,
)
def test_rag(test_case: LLMTestCase):
    answer_relevancy_metric = AnswerRelevancyMetric(model="gpt-3.5-turbo")
    faithfulness_metric = FaithfulnessMetric(model="gpt-3.5-turbo")
    context_relevancy_metric = ContextualRelevancyMetric(model="gpt-3.5-turbo")
    assert_test(
        test_case,
        [answer_relevancy_metric, faithfulness_metric, context_relevancy_metric],
    )
In this example, we: 在这个例子中，我们

Construct a test dataset containing questions, generated answers, contexts, and ground truth.
构建一个测试数据集，其中包含问题、生成的答案、上下文和基本事实。
Use metrics like Faithfulness, Answer Relevance, and Context Relevance.
使用 Faithfulness 、 Answer Relevance 和 Context Relevance 等指标。
DeepEval uses gpt-4 by default, but for cost efficiency, you can specify other models like gpt-3.5-turbo.
DeepEval 默认使用 gpt-4 ，但为了节约成本，您可以指定其他模型，如 gpt-3.5-turbo 。
The threshold for evaluation metrics is set to 0.5 by default, indicating that scores below this value signify failed tests.
评估指标的阈值默认设置为 0.5，低于该值表示测试失败。
Run the test file with deepeval test run test_deepeval.py to execute the evaluation tasks. DeepEval outputs evaluation results in the terminal. If the test passes, you'll see PASSED; if not, FAILED.
用 deepeval test run test_deepeval.py 运行测试文件，执行评估任务。DeepEval 会在终端输出评估结果。如果测试通过，则显示 PASSED ；如果未通过，则显示 FAILED 。


Evaluation Results 评估结果
While terminal results can be inconvenient to view, DeepEval provides alternative ways to access evaluation results. You can save them to a local JSON file by setting the environment variable export DEEPEVAL_RESULTS_FOLDER="./output". This saves the results in the specified folder.
虽然终端结果可能不便查看，但 DeepEval 提供了其他访问评估结果的方法。您可以通过设置环境变量 export DEEPEVAL_RESULTS_FOLDER="./output" 将结果保存到本地 JSON 文件。这会将结果保存到指定的文件夹中。

Another way to view results is through the Confident platform. Log in using your API key with deepeval login --confident-api-key your_api_key, then run the test. Results are automatically uploaded to the Confident platform, making them easier to view. Here's a screenshot of the evaluation results on Confident:
另一种查看结果的方法是通过 Confident 平台。使用带有 deepeval login --confident-api-key your_api_key 的 API 密钥登录，然后运行测试。结果会自动上传到 Confident 平台，使其更易于查看。下面是 Confident 上评估结果的截图：


Confident also allows you to export results as CSV files for local viewing:
Confident 还允许您将结果导出为 CSV 文件，以便在本地查看：


UpTrain 向上培训
UpTrain is an open-source platform for evaluating and improving LLM applications. It has the most extensive set of evaluation metrics among the tools discussed here.
UpTrain 是一个用于评估和改进 LLM 应用程序的开源平台。在本文讨论的工具中，它拥有最广泛的评估指标集。


Image source: https://github.com/uptrain-ai/uptrain
图片来源：https://github.com/uptrain-ai/uptrain
Evaluation Metrics 评估指标
UpTrain’s evaluation metrics apply to both RAG applications and other LLM applications. Here are some metrics:
UpTrain 的评估指标既适用于 RAG 应用程序，也适用于其他 LLM 应用程序。下面是一些指标：

Response Matching: Assesses the consistency between Answer and Ground Truth.
响应匹配：评估 Answer 和 Ground Truth 之间的一致性。
Response Completeness: Measures whether Answer addresses all aspects of Question.
答复完整性：衡量 Answer 是否涉及 Question 的所有方面。
Response Conciseness: Checks if Answer contains unrelated content.
响应简洁性：检查 Answer 是否包含无关内容。
Response Relevance: Evaluate the relevance between Answer and Question.
回应相关性：评估 Answer 和 Question 之间的相关性。
Response Validity: Assesses whether Answer is valid, avoiding responses like "I don't know."
回复有效性：评估 Answer 是否有效，避免 "我不知道 "之类的回答。
Response Consistency: Evaluates consistency between Answer, Question, and Context.
响应一致性：评估 Answer 、 Question 和 Context 之间的一致性。
Context Relevance: Measures the relevance between Context and Question.
上下文相关性：衡量 Context 和 Question 之间的相关性。
Context Utilization: Evaluate if Answer utilizes Context to address all points.
语境利用：评估 Answer 是否利用 Context 来解决所有问题。
Factual Accuracy: Checks if Answer is factually accurate and derived from Context.
事实准确性：检查 Answer 是否与事实相符，是否源于 Context 。
Context Conciseness: Measures if Context is concise and avoids irrelevant information.
语境简洁性：衡量 Context 是否简明扼要，避免无关信息。
Context Reranking: Assesses the effectiveness of reranked Context.
重新排名：评估重新排名 Context 的有效性。
Jailbreak Detection: Evaluate whether Question contains jailbreak cues.
越狱检测：评估 Question 是否包含越狱线索。
Prompt Injection: Measures that Question could lead to leaking system prompts.
提示注入：采取措施防止 Question 可能导致系统提示泄漏。
Language Features: Assess if Answer is concise, coherent, and free from grammatical errors.
语言特点：评估 Answer 是否简洁、连贯、无语法错误。
Tonality: Checks if Answer aligns with a specific tone.
音调：检查 Answer 是否与特定音调一致。
Sub-query Completeness: Evaluate if sub-questions cover all aspects of Question.
子查询完整性：评估子问题是否涵盖 Question 的所有方面。
Multi-query Accuracy: Evaluate if variations of Question align with the original.
多重查询的准确性：评估 Question 的变化是否与原文一致。
Code Hallucination: Measures if code in Answer is relevant to Context.
代码幻觉：测量 Answer 中的代码是否与 Context 相关。
User Satisfaction: Evaluates user satisfaction in conversations.
用户满意度：评估用户在对话中的满意度。
Usage Example 使用示例
UpTrain integrates with LlamaIndex, allowing you to create evaluation objects with EvalLlamaIndex. Here is an example:
UpTrain 与 LlamaIndex 集成，允许你使用 EvalLlamaIndex 创建评估对象。 下面是一个例子：

import os
import json
from uptrain import EvalLlamaIndex, Evals, ResponseMatching, Settings

settings = Settings(
    openai_api_key=os.getenv("OPENAI_API_KEY"),
)
data = []
for i in range(len(questions)):
    data.append(
        {
            "question": questions[i],
            "ground_truth": ground_truth[i],
        }
    )
llamaindex_object = EvalLlamaIndex(settings=settings, query_engine=query_engine)
results = llamaindex_object.evaluate(
    data=data,
    checks=[
        ResponseMatching(),
        Evals.CONTEXT_RELEVANCE,
        Evals.FACTUAL_ACCURACY,
        Evals.RESPONSE_RELEVANCE,
    ],
)
with open("output/uptrain-evaluate.json", "w") as json_file:
    json.dump(results, json_file, indent=2)
In this example, we: 在这个例子中，我们

Use OpenAI’s API key for UpTrain.
为 UpTrain 使用 OpenAI 的 API 密钥。
The initial dataset only requires Question and Ground Truth. Answer and Context are generated by EvalLlamaIndex.
初始数据集只需要 Question 和 Ground Truth 。 Answer 和 Context 由 EvalLlamaIndex 生成。
Include common evaluation metrics.
包括通用评估指标。
Save the results in a JSON file.
将结果保存在 JSON 文件中。
Evaluation Results 评估结果
The evaluation results are stored in JSON files. To make it easier to compare, convert the results into CSV format. Below is UpTrain’s evaluation results:
评估结果存储在 JSON 文件中。为便于比较，可将结果转换为 CSV 格式。以下是 UpTrain 的评估结果：


In UpTrain’s evaluation results, the Response Matching score can sometimes seem inaccurate. After running Response Matching, you might get three scores: score_response_match, score_response_match_recall, and score_response_match_precision. Even when the Answer and Ground Truth seem similar, these scores might be 0. It's unclear why this happens; if you know, please comment below.
在 UpTrain 的评估结果中， Response Matching 分数有时看起来并不准确。运行 Response Matching 后，你可能会得到三个分数： score_response_match 、 score_response_match_recall 和 score_response_match_precision 。即使 Answer 和 Ground Truth 看起来相似，这些分数也可能是 0。不清楚为什么会出现这种情况；如果你知道，请在下面发表评论。

Comparison Analysis 对比分析

Evaluation Metrics: TruLens has fewer metrics, while DeepEval and UpTrain have a wide range of metrics. Ragas has a moderate number of metrics, covering all key aspects of RAG applications.
评估指标：TruLens 的指标较少，而 DeepEval 和 UpTrain 的指标范围较广。Ragas 的指标数量适中，涵盖了 RAG 应用的所有关键方面。
Custom Evaluations: DeepEval and UpTrain support custom metrics, while TruLens and Ragas do not.
自定义评估：DeepEval 和 UpTrain 支持自定义指标，而 TruLens 和 Ragas 不支持。
Custom LLMs: Most tools support custom LLMs. Ragas implements this through LangChain.
自定义 LLMs：大多数工具都支持自定义 LLMs。Ragas 通过 LangChain 实现了这一点。
Framework Integration: Most tools support integration with LlamaIndex and LangChain, but DeepEval and UpTrain only support LlamaIndex.
框架集成：大多数工具都支持与 LlamaIndex 和 LangChain 集成，但 DeepEval 和 UpTrain 仅支持 LlamaIndex。
WebUI: Web-based interfaces allow easier viewing of results. TruLens, DeepEval, and UpTrain support this; Ragas does not, though you can use third-party tools to view results.
网络用户界面：基于网络的界面可以更方便地查看结果。TruLens、DeepEval 和 UpTrain 支持 WebUI；Ragas 不支持，不过您可以使用第三方工具查看结果。
Explanation of Scores: All tools except Ragas provide reasons for scores. DeepEval can help Ragas generate these explanations.
分数说明：除 Ragas 外，所有工具都会提供评分理由。DeepEval 可以帮助 Ragas 生成这些解释。
Unit Testing: DeepEval offers unit test-like evaluation tasks, unique among these tools.
单元测试：DeepEval 提供类似单元测试的评估任务，这在这些工具中是独一无二的。
TruLens and Ragas are among the first RAG evaluation tools, with DeepEval and UpTrain emerging later. These newer tools likely draw inspiration from the earlier ones, leading to more comprehensive metrics and improved functionality. However, TruLens and Ragas still have unique advantages, such as TruLens’s intuitive results and Ragas’s tailored metrics for RAG applications.
TruLens 和 Ragas 是最早的 RAG 评估工具，DeepEval 和 UpTrain 则是后来出现的。这些较新的工具可能从早期的工具中汲取了灵感，从而获得了更全面的指标和更完善的功能。不过，TruLens 和 Ragas 仍然具有独特的优势，例如 TruLens 的直观结果和 Ragas 为 RAG 应用量身定制的指标。

Conclusion 结论
This article discussed various RAG evaluation tools that integrate with LlamaIndex and compared their features. These tools help developers better understand and optimize RAG applications. There are other tools not mentioned here, like LlamaIndex’s built-in evaluation tool and Tonic Validate. If you’re unsure which evaluation tool to choose, start with one and use it in a project. If it doesn’t meet your needs, try another one.
本文讨论了与 LlamaIndex 集成的各种 RAG 评估工具，并对其功能进行了比较。这些工具可帮助开发人员更好地了解和优化 RAG 应用程序。还有其他一些工具没有在此提及，如 LlamaIndex 的内置评估工具和 Tonic Validate。如果你不确定选择哪种评估工具，可以先从其中一种开始，并在一个项目中使用它。如果它不能满足你的需求，那就试试其他的。