# Visual Question Answering (VQA) Project

This project focuses on developing a Visual Question Answering (VQA) model using fine-tuned pre-trained models and leveraging the efficiency of Low-Rank Adaptation (LoRA).

## Dataset Handling

### Loading the Dataset on Kaggle
1. **Load the Dataset**: We download 25% of the dataset from Hugging Face, which takes around 20-25 minutes and consumes nearly 60 GB of disk space.
2. **Save the Dataset**: The dataset is saved as Arrow files to optimize read and write speeds.
3. **Save the Notebook Version**: This ensures that the dataset and output are stored.
4. **Create a New Dataset on Kaggle**: The saved dataset is uploaded as a new dataset on Kaggle.
5. **Add the Dataset to the Notebook**: The new dataset is added and loaded efficiently, using around 18 GB of disk space.

### Data Analysis
We analyzed the dataset to understand answer types and their frequencies, focusing on:
- **Question Types**: Distribution of question types.
- **Answer Lengths**: Number of words in the answers.
- **Colour Terms**: Frequency of colour terms.
- **Animal Terms**: Frequency of animal-related terms.
- **People Terms**: Frequency of people-related terms.

## Data Preprocessing
### Image Preprocessing
Images are resized to 224x224 pixels and converted to PyTorch tensors.

### Text Preprocessing
Questions are tokenized using the BERT tokenizer, converting text into token IDs.

### Dataset Classes
A custom `VQADataset` class handles the preprocessing of images and text, and extracts image features using a Vision Transformer (ViT).

## Model 1: Baseline Model
### Architecture
- **Vision Transformer (ViT)**: Used for image feature extraction.
- **BERT**: Used for text feature extraction.
- **Feature Projection and Attention Mechanism**: Combines image and text features using linear layers and attention mechanisms.
- **Feature Combination and Decoder**: Combines features to predict answers using a final linear layer.

### Training
- **Data Preparation**: Splitting into training, validation, and test sets.
- **Model Training**: Training for 15 epochs on 10k dataset, taking 1 hour and 39 minutes.

### Evaluation
- **Metrics**: Evaluated using accuracy, precision, recall, and F1-score.

## Model 2: LoRA Fine-Tuning with Transformer Decoder
### Architecture
- **Similarities**: Same ViT and BERT architecture as Model 1.
- **Differences**: Incorporates LoRA, uses a Transformer decoder for feature refinement, and includes a final linear classification layer.

### Training
- **Process**: Similar to Model 1 with the addition of LoRA for enhancing feature extraction.

### Evaluation
- **Metrics**: Similar to Model 1.

## Observations
- **Model 1**: Performs well on yes/no questions but tends to overfit binary categories.
- **Model 2**: Better with numbers, colors, and directions but sometimes struggles with unknown words and relative outputs.

This summary provides an overview of the VQA project's workflow, data handling, model architectures, and key observations. This README.md file serves as a concise guide for understanding the project's structure and outcomes.
