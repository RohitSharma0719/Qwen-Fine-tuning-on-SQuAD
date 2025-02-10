# Qwen-Fine-tuning-on-SQuAD
This repository contains a script to fine-tune the Qwen-1.5-0.5B-Chat model on the SQuAD dataset using Low-Rank Adaptation (LoRA). The fine-tuning process optimizes the model for question-answering tasks while maintaining efficiency.

Overview

Model: Qwen-1.5-0.5B-Chat

Dataset: SQuAD (Stanford Question Answering Dataset)

Frameworks Used: Hugging Face Transformers, PEFT (Parameter Efficient Fine-Tuning), PyTorch

Steps Performed

1. Import Necessary Libraries

We use Hugging Face's transformers and datasets libraries to load the model and dataset. The peft library is used for LoRA-based fine-tuning.

2. Load and Preprocess the Dataset

The SQuAD dataset is loaded using the datasets library.

A subset (40%) of the training and validation sets is taken for faster fine-tuning.

The dataset is tokenized using the Qwen tokenizer, with padding and truncation applied.

Answer span positions are computed to align with token positions.

3. Load the Pre-Trained Model

The Qwen-1.5-0.5B-Chat model and its tokenizer are loaded with trust_remote_code=True.

LoRA is applied to the model to optimize its query (q_proj) and value (v_proj) projection layers.


4. Define Training Parameters

Batch Size: 8 per device

Learning Rate: 2e-5

Epochs: 3

Weight Decay: 0.01

Evaluation Strategy: Per epoch

Precision: FP16 for faster training

Logging: Logs are saved every 10 steps

Saving Strategy: Model checkpoints saved per epoch

5. Fine-Tune the Model

The Hugging Face Trainer class is used to handle the fine-tuning process. The model is trained and evaluated using the tokenized dataset, and LoRA allows efficient parameter tuning with minimal computational overhead.
