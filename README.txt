# Graph-Based Prediction for TruthfulQA

> This work was conducted by Somin Lee (20230508, [dlthals0404@kaist.ac.kr](mailto:dlthals0404@kaist.ac.kr)) and Seunguk Lee (20230513, [sulee04@kaist.ac.kr](mailto:sulee04@kaist.ac.kr)) as the term project for the Spring 2025 offering of KAIST CS471: Graph Machine Learning and Mining.
>
> *Both authors contributed equally to this work.

While artificial intelligence is achieving great success across diverse fields, answering true/false questions—such as those found in the [TruthfulQA](https://arxiv.org/abs/2109.07958) dataset—remains a significant challenge, despite the task’s seemingly simple format. A common approach in recent AI development has been to feed the entire problem into a large language model (LLM) and observe the outcome. However, even advanced models like GPT-4 reportedly struggle with this task, reaching only around 60% accuracy—barely outperforming random guessing.

We propose a GNN-based approach to answering complex true/false questions. By modeling questions and answers as nodes in a graph and representing their semantic relationships as edges, our method captures the underlying logical and contextual structure that traditional LLM-only pipelines often overlook. This setup allows the Graph Neural Network to learn patterns of factual consistency and contradiction, ultimately enabling more reliable truth estimation beyond surface-level language patterns.

## Dataset

We use the **TruthfulQA** benchmark, structured as a graph where:

- **Nodes**: All sentences (*question*, *correct*, *incorrect*); augmented with 384-dim Sentence-BERT embeddings.
- **Edges**: From question to answers; labeled 1 for correct, 0 for incorrect
- **Scale**: 6,819 nodes, 6,029 edges
- **Task**: Binary edge prediction (truthfulness)
- **Split**: Inductive 70 % / 15 % / 15 % (train/val/test)

## Project Structure

- **README.md** provides a brief overview of this project.
- **research_20230508_SominLee_20230513_SeungukLee_poster.pdf** and **research_20230508_SominLee_20230513_SeungukLee_poster.pptx** is our poster.
- **notebook1_evaluation_of_graph_models.ipynb** contains our proposed model and its evaluation methods. This code can be used to reproduce the *Accuracy, Precision, Recall, F1: Model Comparison* section of the poster.
- **notebook2_robustness_to_label_noise**.ipynb contains our strategy to compare the robustness of a neural net model and a GNN model. This code can be used to reproduce the *Robustness to Label Noise* section of the poster.
- **TruthfulQA.csv** is the original source of data for our work. Refer to the [paper](https://arxiv.org/abs/2109.07958) for more details. This dataset is distributed under Apache License 2.0.
- **noise_experiment_results.csv** contains the raw data produced by Notebook 1.

## Note

- We strongly recommend running the notebook in a GPU-supported Colab environment. Otherwise, execution will take a significant amount of time.
- The results may slightly vary due to the use of non-deterministic algorithms.

## License

This project is licensed under the [Creative Commons Attribution-ShareAlike 3.0](https://creativecommons.org/licenses/by-sa/3.0/) license (CC BY-SA 3.0).