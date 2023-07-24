# Recent Papers Related to AI Related Security <!-- omit from toc --> 

<!-- ## All Papers (Classification according to Publication) -->


## All Papers (Classification according to Subject) <!-- omit from toc --> 
- [Fuzzing Test Case Generation (Traditional AI Method)](#fuzzing-test-case-generation-traditional-ai-method)
  - [Neuzz: Efficient fuzzing with neural program smoothing, *SP‘19, Dongdong She*](#neuzz-efficient-fuzzing-with-neural-program-smoothing-sp19-dongdong-she)
  - [MTFuzz: Fuzzing with a multi-task neural network, *ECSE/FSE‘20, Dongdong She*](#mtfuzz-fuzzing-with-a-multi-task-neural-network-ecsefse20-dongdong-she)
  - [Evaluating and Improving Neural Program-Smoothing-based Fuzzing, *ICSE’22, Lingming Zhang*](#evaluating-and-improving-neural-program-smoothing-based-fuzzing-icse22-lingming-zhang)
- [Unit Test Case Generation (Traditional AI Method)](#unit-test-case-generation-traditional-ai-method)
  - [Unit Test Case Generation with Transformers and Focal Context, *Arxiv’20, Microsoft*](#unit-test-case-generation-with-transformers-and-focal-context-arxiv20-microsoft)
- [Unit Test Generation (LLM)](#unit-test-generation-llm)
  - [Code Generation Tools (Almost) for Free? A Study of Few-Shot, Pre-Trained Language Models on Code, *Arxiv’22*](#code-generation-tools-almost-for-free-a-study-of-few-shot-pre-trained-language-models-on-code-arxiv22)
  - [ChatUniTest: a ChatGPT-based automated unit test generation tool, *Arxiv'23*](#chatunitest-a-chatgpt-based-automated-unit-test-generation-tool-arxiv23)
  - [Codamosa: Escaping coverage plateaus in test generation with pre-trained large language models, *ICSE’23, Caroline Lemieux*](#codamosa-escaping-coverage-plateaus-in-test-generation-with-pre-trained-large-language-models-icse23-caroline-lemieux)
- [Fuzz (LLM)](#fuzz-llm)
  - [Large language models are edge-case fuzzers: Testing deep learning libraries via FuzzGPT, *Arxiv’23, Lingming Zhang*\]](#large-language-models-are-edge-case-fuzzers-testing-deep-learning-libraries-via-fuzzgpt-arxiv23-lingming-zhang)
  - [Augmenting Greybox Fuzzing with Generative AI, *Arxiv’23, Heng Yin*](#augmenting-greybox-fuzzing-with-generative-ai-arxiv23-heng-yin)
- [Code Representation](#code-representation)
  - [Convolutional Neural Networks over Tree Structures for Programming Language Processing, *AAAI'16*](#convolutional-neural-networks-over-tree-structures-for-programming-language-processing-aaai16)
  - [Graphcodebert: Pre-training code representations with data flow, *ICLR'21, Microsoft Research Asia*](#graphcodebert-pre-training-code-representations-with-data-flow-iclr21-microsoft-research-asia)
  - [Structcoder: Structure-aware transformer for code generation, *arXiv'22*](#structcoder-structure-aware-transformer-for-code-generation-arxiv22)
  - [Unixcoder: Unified crossmodal pre-training for code representation, *ACL'22*](#unixcoder-unified-crossmodal-pre-training-for-code-representation-acl22)
- [Code Generation](#code-generation)
  - [Jigsaw: Large Language Models meet Program Synthesis, *ICSE’22, Microsoft*](#jigsaw-large-language-models-meet-program-synthesis-icse22-microsoft)
  - [Competition-level code generation with alphacode, *Science'22*](#competition-level-code-generation-with-alphacode-science22)
- [Program Analysis](#program-analysis)
  - [ProGraML: Graph-based Deep Learning for Program Optimization and Analysis, *Arxiv'20*](#programl-graph-based-deep-learning-for-program-optimization-and-analysis-arxiv20)


## Fuzzing Test Case Generation (Traditional AI Method)

### Neuzz: Efficient fuzzing with neural program smoothing, *SP‘19, Dongdong She*
- [Paper](https://arxiv.org/abs/1807.05620)
- [Code](https://github.com/dongdongshe/neuzz) 

> Smooth edge coverage  
> 2 Dense + 2 Activation

**Abstract:** Fuzzing has become the de facto standard technique for finding software vulnerabilities. However, even state-of-the- art fuzzers are not very efficient at finding hard-to-trigger software bugs. Most popular fuzzers use evolutionary guidance to generate inputs that can trigger different bugs. Such evolutionary algorithms, while fast and simple to implement, often get stuck in fruitless sequences of random mutations. Gradient-guided optimization presents a promising alternative to evolutionary guidance. Gradient-guided techniques have been shown to significantly outperform evolutionary algorithms at solving high-dimensional structured optimization problems in domains like machine learning by efficiently utilizing gradients or higher-order derivatives of the underlying function.
However, gradient-guided approaches are not directly applicable to fuzzing as real-world program behaviors contain many discontinuities, plateaus, and ridges where the gradient- based methods often get stuck. We observe that this problem can be addressed by creating a smooth surrogate function approximating the target program’s discrete branching behavior. In this paper, we propose a novel program smoothing technique using surrogate neural network models that can incrementally learn smooth approximations of a complex, real-world program’s branching behaviors. We further demonstrate that such neural network models can be used together with gradient-guided input generation schemes to significantly increase the efficiency of the fuzzing process.
Our extensive evaluations demonstrate that NEUZZ significantly outperforms 10 state-of-the-art graybox fuzzers on 10 popular real-world programs both at finding new bugs and achieving higher edge coverage. NEUZZ found 31 previously unknown bugs (including two CVEs) that other fuzzers failed to find in 10 real-world programs and achieved 3X more edge coverage than all of the tested graybox fuzzers over 24 hour runs. Furthermore, NEUZZ also outperformed existing fuzzers on both LAVA-M and DARPA CGC bug datasets.

### MTFuzz: Fuzzing with a multi-task neural network, *ECSE/FSE‘20, Dongdong She*
- [Paper](https://arxiv.org/abs/2005.12392)
- [Code](https://github.com/rahlk/MTFuzz)

> Call Stack + Edge Coverage  
> 4 Dense + 4 Activation

**Abstract:** Fuzzing is a widely used technique for detecting software bugs and vulnerabilities. Most popular fuzzers generate new inputs using an evolutionary search to maximize code coverage. Essentially, these fuzzers start with a set of seed inputs, mutate them to generate new inputs, and identify the promising inputs using an evolutionary fitness function for further mutation. Despite their success, evolutionary fuzzers tend to get stuck in long sequences of unproductive mutations. In recent years, machine learning (ML) based mutation strategies have reported promising results. However, the existing ML-based fuzzers are limited by the lack of quality and diversity of the training data. As the input space of the target programs is high dimensional and sparse, it is prohibitively expensive to collect many diverse samples demonstrating successful and unsuccessful mutations to train the model. In this paper, we address these issues by using a Multi-Task Neural Network that can learn a compact embedding of the input space based on diverse training samples for multiple related tasks (i.e., predicting for different types of coverage). The compact embedding can guide the mutation process by focusing most of the mutations on the parts of the embedding where the gradient is high. MTFuzz uncovers 11 previously unseen bugs and achieves an average of 2× more edge coverage compared with 5 state-of-the-art fuzzer on 10 real-world programs.

### Evaluating and Improving Neural Program-Smoothing-based Fuzzing, *ICSE’22, Lingming Zhang*
- [Paper](https://i.cs.hku.hk/~heming/papers/icse22-program-smooth-fuzzing.pdf)
- [Code](https://github.com/PoShaung/program-smoothing-fuzzing)

> Improving Neuzz & MTFuzz  
> Resource-Efficient Edge Selection Mechanism  
> Probabilistic Byte Selection Mechanism

**Abstract:** Fuzzing nowadays has been commonly modeled as an optimization problem, e.g., maximizing code coverage under a given time budget via typical search-based solutions such as evolutionary algorithms. However, such solutions are widely argued to cause inefficient computing resource usage, i.e., inefficient mutations. To address this issue, two neural program-smoothing-based fuzzers, Neuzz and MTFuzz, have been recently proposed to approximate program branching behaviors via neural network models, which input byte sequences of a seed and output vectors representing program branching behaviors. Moreover, assuming that mutating the bytes with larger gradients can better explore branching behaviors, they develop strategies to mutate such bytes for generating new seeds as test cases. Meanwhile, although they have been shown to be effective in the original papers, they were only evaluated upon a limited dataset. In addition, it is still unclear how their key technical components and whether other factors can impact fuzzing performance. To further investigate neural program-smoothing-based fuzzing, we first construct a large-scale benchmark suite with a total of 28 popular open-source projects. Then, we extensively evaluate Neuzz and MTFuzz on such benchmarks. The evaluation results suggest that their edge coverage performance can be unstable. Moreover, neither neural network models nor mutation strategies can be consistently effective, and the power of their gradient-guidance mechanisms have been compromised. Inspired by such findings, we propose a simplistic technique, PreFuzz, which improves neural program-smoothing-based fuzzers with a resource-efficient edge selection mechanism to enhance their gradient guidance and a probabilistic byte selection mechanism to further boost mutation effectiveness. Our evaluation results indicate that PreFuzz can significantly increase the edge coverage of Neuzz/MTFuzz, and also reveal multiple practical guidelines to advance future research on neural program-smoothing-based fuzzing.

## Unit Test Case Generation (Traditional AI Method)

### Unit Test Case Generation with Transformers and Focal Context, *Arxiv’20, Microsoft*
- [Paper](https://arxiv.org/abs/2009.05617)
- [Code](https://github.com/microsoft/methods2test)

> BART

**Abstract:** Automated unit test case generation tools facilitate test-driven development and support developers by suggesting tests intended to identify flaws in their code. Existing approaches are usually guided by the test coverage criteria, generating synthetic test cases that are often difficult for developers to read or understand. In this paper we propose AthenaTest, an approach that aims to generate unit test cases by learning from real-world focal methods and developer-written testcases. We formulate unit test case generation as a sequence-to-sequence learning task, adopting a two-step training procedure consisting of denoising pretraining on a large unsupervised Java corpus, and supervised finetuning for a downstream translation task of generating unit tests. We investigate the impact of natural language and source code pretraining, as well as the focal context information surrounding the focal method. Both techniques provide improvements in terms of validation loss, with pretraining yielding 25% relative improvement and focal context providing additional 11.1% improvement. We also introduce Methods2Test, the largest publicly available supervised parallel corpus of unit test case methods and corresponding focal methods in Java, which comprises 780K test cases mined from 91K open-source repositories from GitHub. We evaluate AthenaTest on five defects4j projects, generating 25K passing test cases covering 43.7% of the focal methods with only 30 attempts. We execute the test cases, collect test coverage information, and compare them with test cases generated by EvoSuite and GPT-3, finding that our approach outperforms GPT-3 and has comparable coverage w.r.t. EvoSuite. Finally, we survey professional developers on their preference in terms of readability, understandability, and testing effectiveness of the generated tests, showing overwhelmingly preference towards AthenaTest.

## Unit Test Generation (LLM)

### Code Generation Tools (Almost) for Free? A Study of Few-Shot, Pre-Trained Language Models on Code, *Arxiv’22*
- [Paper](https://arxiv.org/abs/2206.01335)

> Codex for Unit Test Generation

**Abstract:** Few-shot learning with large-scale, pre-trained language models is a powerful way to answer questions about code, e.g., how to complete a given code example, or even generate code snippets from scratch. The success of these models raises the question whether they could serve as a basis for building a wide range code generation tools. Traditionally, such tools are built manually and separately for each task. Instead, few-shot learning may allow to obtain different tools from a single pre-trained language model by simply providing a few examples or a natural language description of the expected tool behavior. This paper studies to what extent a state-of-the-art, pre-trained language model of code, Codex, may serve this purpose. We consider three code manipulation and code generation tasks targeted by a range of traditional tools: (i) code mutation; (ii) test oracle generation from natural language documentation; and (iii) test case generation. For each task, we compare few-shot learning to a manually built tool. Our results show that the model-based tools complement (code mutation), are on par (test oracle generation), or even outperform their respective traditionally built tool (test case generation), while imposing far less effort to develop them. By comparing the effectiveness of different variants of the model-based tools, we provide insights on how to design an appropriate input ("prompt") to the model and what influence the size of the model has. For example, we find that providing a small natural language description of the code generation task is an easy way to improve predictions. Overall, we conclude that few-shot language models are surprisingly effective, yet there is still more work to be done, such as exploring more diverse ways of prompting and tackling even more involved tasks.

### ChatUniTest: a ChatGPT-based automated unit test generation tool, *Arxiv'23*
- [Paper](https://arxiv.org/abs/2305.04764)
- [Code](https://github.com/ZJU-ACES-ISE/chatunitest-maven-plugin)

> ChatGPT for Unit Test Generation

**Abstract:** Unit testing is a crucial, yet often tedious and time-consuming task. To relieve developers from this burden, automated unit test generation techniques are developed. Existing automated unit test generation tools, such as program-analysis-based tools like EvoSuite and Randoop, lack program comprehension, resulting in unit tests with poor readability and limited assertions. Language-model-based tools, such as AthenaTest and A3Test, have limitations in the generation of correct unit tests. In this paper, we introduce ChatUniTest, a ChatGPT-based automated unit test generation tool developed under the Generation-Validation-Repair framework. ChatUniTest generates tests by parsing the project, extracting essential information, and creating an adaptive focal context that includes the focal method and its dependencies within the pre-defined maximum prompt token limit. The context is incorporated into a prompt and subsequently submitted to ChatGPT. Once ChatGPT's response is received, ChatUniTest proceeds to extract the raw test from the response. It then validates the test and employs rule-based repair to fix syntactic and simple compile errors, followed by ChatGPT-based repair to address challenging errors. Our rigorous evaluation demonstrates that ChatUniTest outperforms EvoSuite in branch and line coverage, surpasses AthenaTest and A3Test in focal method coverage, and effectively generates assertions while utilizing mock objects and reflection to achieve test objectives.

### Codamosa: Escaping coverage plateaus in test generation with pre-trained large language models, *ICSE’23, Caroline Lemieux*
- [Paper](https://www.carolemieux.com/codamosa_icse23.pdf)
- [Code](https://github.com/microsoft/codamosa)

**Abstract:** Search-based software testing (SBST) generates high-coverage test cases for programs under test with a combination of test case generation and mutation. SBST’s performance relies on there being a reasonable probability of generating test cases that exercise the core logic of the program under test. Given such test cases, SBST can then explore the space around them to exercise various parts of the program. This paper explores whether Large Language Models (LLMs) of code, such as OpenAI’s Codex, can be used to help SBST’s exploration. Our proposed algorithm, CODAMOSA, conducts SBST until its coverage improvements stall, then asks Codex to provide example test cases for under-covered functions. These examples help SBST redirect its search to more useful areas of the search space. On an evaluation over 486 benchmarks, CODAMOSA achieves statistically significantly higher coverage on many more benchmarks (173 and 279) than it reduces coverage on (10 and 4), compared to SBST and LLM-only baselines.

## Fuzz (LLM)

### Large language models are edge-case fuzzers: Testing deep learning libraries via FuzzGPT, *Arxiv’23, Lingming Zhang*]
- [Paper](https://arxiv.org/abs/2304.02014)
<!-- - [Code]() -->

> Fuzz Driver Generated by LLM  
> Historical bug information given

**Abstract:** Deep Learning (DL) library bugs affect downstream DL applications, emphasizing the need for reliable systems. Generating valid input programs for fuzzing DL libraries is challenging due to the need for satisfying both language syntax/semantics and constraints for constructing valid computational graphs. Recently, the TitanFuzz work demonstrates that modern Large Language Models (LLMs) can be directly leveraged to implicitly learn all the constraints to generate valid DL programs for fuzzing. However, LLMs tend to generate ordinary programs following similar patterns seen in their massive training corpora, while fuzzing favors unusual inputs that cover edge cases or are unlikely to be manually produced.
To fill this gap, this paper proposes FuzzGPT, the first technique to prime LLMs to synthesize unusual programs for fuzzing. FuzzGPT is built on the well-known hypothesis that historical bug-triggering programs may include rare/valuable code ingredients important for bug finding. Traditional techniques leveraging such historical information require intensive human efforts to design dedicated generators and ensure the validity of generated programs. FuzzGPT demonstrates that this process can be fully automated via the intrinsic capabilities of LLMs (including fine-tuning and in-context learning), while being generalizable and applicable to challenging domains. While FuzzGPT can be applied with different LLMs, this paper focuses on the powerful GPT-style models: Codex and CodeGen. Moreover, FuzzGPT also shows the potential of directly leveraging the instruct-following capability of the recent ChatGPT for effective fuzzing. Evaluation on two popular DL libraries (PyTorch and TensorFlow) shows that FuzzGPT can substantially outperform TitanFuzz, detecting 76 bugs, with 49 already confirmed as previously unknown bugs, including 11 high-priority bugs or security vulnerabilities.

### Augmenting Greybox Fuzzing with Generative AI, *Arxiv’23, Heng Yin*
- [Paper](https://arxiv.org/abs/2306.06782)
- [Code]() Publish upon acceptance

> Apply ChatGPT for Seed Generation + Mutation

**Abstract:** Real-world programs expecting structured inputs often has a format-parsing stage gating the deeper program space. Neither a mutation-based approach nor a generative approach can provide a solution that is effective and scalable. Large language models (LLM) pre-trained with an enormous amount of natural language corpus have proved to be effective for understanding the implicit format syntax and generating format-conforming inputs. In this paper, propose ChatFuzz, a greybox fuzzer augmented by generative AI. More specifically, we pick a seed in the fuzzer's seed pool and prompt ChatGPT generative models to variations, which are more likely to be format-conforming and thus of high quality. We conduct extensive experiments to explore the best practice for harvesting the power of generative LLM models. The experiment results show that our approach improves the edge coverage by 12.77\% over the SOTA greybox fuzzer (AFL++) on 12 target programs from three well-tested benchmarks. As for vulnerability detection, \sys is able to perform similar to or better than AFL++ for programs with explicit syntax rules but not for programs with non-trivial syntax.

## Code Representation

### Convolutional Neural Networks over Tree Structures for Programming Language Processing, *AAAI'16*
- [Paper](https://ojs.aaai.org/index.php/AAAI/article/view/10139)
<!-- - [Code]() -->

> AST Based

**Abstract:** Programming language processing (similar to natural language processing) is a hot research topic in the field of software engineering; it has also aroused growing interest in the artificial intelligence community. However, different from a natural language sentence, a program contains rich, explicit, and complicated structural information. Hence, traditional NLP models may be inappropriate for programs. In this paper, we propose a novel tree-based convolutional neural network (TBCNN) for programming language processing, in which a convolution kernel is designed over programs' abstract syntax trees to capture structural information. TBCNN is a generic architecture for programming language processing; our experiments show its effectiveness in two different program analysis tasks: classifying programs according to functionality, and detecting code snippets of certain patterns. TBCNN outperforms baseline methods, including several neural models for NLP.

### Graphcodebert: Pre-training code representations with data flow, *ICLR'21, Microsoft Research Asia*

- [Paper](https://arxiv.org/abs/2009.08366)
- [Code](https://github.com/microsoft/CodeBERT)

> CFG+DFG Based

**Abstract:** Pre-trained models for programming language have achieved dramatic empirical improvements on a variety of code-related tasks such as code search, code completion, code summarization, etc. However, existing pre-trained models regard a code snippet as a sequence of tokens, while ignoring the inherent structure of code, which provides crucial code semantics and would enhance the code understanding process. We present GraphCodeBERT, a pre-trained model for programming language that considers the inherent structure of code. Instead of taking syntactic-level structure of code like abstract syntax tree (AST), we use data flow in the pre-training stage, which is a semantic-level structure of code that encodes the relation of "where-the-value-comes-from" between variables. Such a semantic-level structure is neat and does not bring an unnecessarily deep hierarchy of AST, the property of which makes the model more efficient. We develop GraphCodeBERT based on Transformer. In addition to using the task of masked language modeling, we introduce two structure-aware pre-training tasks. One is to predict code structure edges, and the other is to align representations between source code and code structure. We implement the model in an efficient way with a graph-guided masked attention function to incorporate the code structure. We evaluate our model on four tasks, including code search, clone detection, code translation, and code refinement. Results show that code structure and newly introduced pre-training tasks can improve GraphCodeBERT and achieves state-of-the-art performance on the four downstream tasks. We further show that the model prefers structure-level attentions over token-level attentions in the task of code search.

### Structcoder: Structure-aware transformer for code generation, *arXiv'22*
- [Paper](https://arxiv.org/abs/2206.05239)
- [Code](https://github.com/reddy-lab-code-research/StructCoder/)

> AST Based

**Abstract:** There has been a recent surge of interest in automating software engineering tasks using deep learning. This paper addresses the problem of code generation where the goal is to generate target code given source code in a different language or a natural language description. Most of the state-of-the-art deep learning models for code generation use training strategies primarily designed for natural language. However, understanding and generating code requires a more rigorous comprehension of the code syntax and semantics. With this motivation, we develop an encoder-decoder Transformer model where both the encoder and decoder are explicitly trained to recognize the syntax and data flow in the source and target codes, respectively. We not only make the encoder structure-aware by leveraging the source code's syntax tree and data flow graph, but we also support the decoder in preserving the syntax and data flow of the target code by introducing two novel auxiliary tasks: AST (Abstract Syntax Tree) paths prediction and data flow prediction. To the best of our knowledge, this is the first work to introduce a structure-aware Transformer decoder that models both syntax and data flow to enhance the quality of generated code. The proposed StructCoder model achieves state-of-the-art performance on code translation and text-to-code generation tasks in the CodeXGLUE benchmark, and improves over baselines of similar size on the APPS code generation benchmark. Our code is publicly available at https://github.com/reddy-lab-code-research/StructCoder/.

### Unixcoder: Unified crossmodal pre-training for code representation, *ACL'22*
- [Paper](https://arxiv.org/abs/2203.03850)
<!-- - [Code]() -->

> AST Based

**Abstract:** Pre-trained models for programming languages have recently demonstrated great success on code intelligence. To support both code-related understanding and generation tasks, recent works attempt to pre-train unified encoder-decoder models. However, such encoder-decoder framework is sub-optimal for auto-regressive tasks, especially code completion that requires a decoder-only manner for efficient inference. In this paper, we present UniXcoder, a unified cross-modal pre-trained model for programming language. The model utilizes mask attention matrices with prefix adapters to control the behavior of the model and leverages cross-modal contents like AST and code comment to enhance code representation. To encode AST that is represented as a tree in parallel, we propose a one-to-one mapping method to transform AST in a sequence structure that retains all structural information from the tree. Furthermore, we propose to utilize multi-modal contents to learn representation of code fragment with contrastive learning, and then align representations among programming languages using a cross-modal generation task. We evaluate UniXcoder on five code-related tasks over nine datasets. To further evaluate the performance of code fragment representation, we also construct a dataset for a new task, called zero-shot code-to-code search. Results show that our model achieves state-of-the-art performance on most tasks and analysis reveals that comment and AST can both enhance UniXcoder.

## Code Generation

### Jigsaw: Large Language Models meet Program Synthesis, *ICSE’22, Microsoft*
- [Paper](https://arxiv.org/abs/2112.02969)
- [Code](https://github.com/microsoft/JigsawDataset)

> Assist GPT-3 and Codex to generate correct code

**Abstract:** Large pre-trained language models such as GPT-3, Codex, and Google's language model are now capable of generating code from natural language specifications of programmer intent. We view these developments with a mixture of optimism and caution. On the optimistic side, such large language models have the potential to improve productivity by providing an automated AI pair programmer for every programmer in the world. On the cautionary side, since these large language models do not understand program semantics, they offer no guarantees about quality of the suggested code. In this paper, we present an approach to augment these large language models with post-processing steps based on program analysis and synthesis techniques, that understand the syntax and semantics of programs. Further, we show that such techniques can make use of user feedback and improve with usage. We present our experiences from building and evaluating such a tool jigsaw, targeted at synthesizing code for using Python Pandas API using multi-modal inputs. Our experience suggests that as these large language models evolve for synthesizing code from intent, jigsaw has an important role to play in improving the accuracy of the systems.

### Competition-level code generation with alphacode, *Science'22*
- [Paper](https://arxiv.org/abs/2203.07814)
- [Code/Dataset](https://github.com/deepmind/code_contests)

**Abstract:** Programming is a powerful and ubiquitous problem-solving tool. Developing systems that can assist programmers or even generate programs independently could make programming more productive and accessible, yet so far incorporating innovations in AI has proven challenging. Recent large-scale language models have demonstrated an impressive ability to generate code, and are now able to complete simple programming tasks. However, these models still perform poorly when evaluated on more complex, unseen problems that require problem-solving skills beyond simply translating instructions into code. For example, competitive programming problems which require an understanding of algorithms and complex natural language remain extremely challenging. To address this gap, we introduce AlphaCode, a system for code generation that can create novel solutions to these problems that require deeper reasoning. In simulated evaluations on recent programming competitions on the Codeforces platform, AlphaCode achieved on average a ranking of top 54.3% in competitions with more than 5,000 participants. We found that three key components were critical to achieve good and reliable performance: (1) an extensive and clean competitive programming dataset for training and evaluation, (2) large and efficient-to-sample transformer-based architectures, and (3) large-scale model sampling to explore the search space, followed by filtering based on program behavior to a small set of submissions.

## Program Analysis

### ProGraML: Graph-based Deep Learning for Program Optimization and Analysis, *Arxiv'20*
- [Paper](https://arxiv.org/abs/2003.10536)
- [Code](https://github.com/ChrisCummins/ProGraML)

**Abstract:** The increasing complexity of computing systems places a tremendous burden on optimizing compilers, requiring ever more accurate and aggressive optimizations. Machine learning offers significant benefits for constructing optimization heuristics but there remains a gap between what state-of-the-art methods achieve and the performance of an optimal heuristic. Closing this gap requires improvements in two key areas: a representation that accurately captures the semantics of programs, and a model architecture with sufficient expressiveness to reason about this representation.
We introduce ProGraML - Program Graphs for Machine Learning - a novel graph-based program representation using a low level, language agnostic, and portable format; and machine learning models capable of performing complex downstream tasks over these graphs. The ProGraML representation is a directed attributed multigraph that captures control, data, and call relations, and summarizes instruction and operand types and ordering. Message Passing Neural Networks propagate information through this structured representation, enabling whole-program or per-vertex classification tasks.
ProGraML provides a general-purpose program representation that equips learnable models to perform the types of program analysis that are fundamental to optimization. To this end, we evaluate the performance of our approach first on a suite of traditional compiler analysis tasks: control flow reachability, dominator trees, data dependencies, variable liveness, and common subexpression detection. On a benchmark dataset of 250k LLVM-IR files covering six source programming languages, ProGraML achieves an average 94.0 F1 score, significantly outperforming the state-of-the-art approaches. We then apply our approach to two high-level tasks - heterogeneous device mapping and program classification - setting new state-of-the-art performance in both.