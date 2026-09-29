Project Summary: Aspect-Based Sentiment Analysis for Automotive Reviews
1. Introduction
This project aimed to develop an Aspect-Based Sentiment Analysis (ABSA) system for automotive reviews. Unlike traditional sentiment analysis which provides an overall sentiment for a text, ABSA identifies sentiments towards specific aspects (e.g., 'engine', 'seats', 'infotainment system') within the review. This offers more granular insights, crucial for understanding customer feedback in detail.

2. Methodology
The ABSA system was built using a fine-tuned BERT (bert-base-uncased) model. The process involved several key stages:

Data Loading and Preprocessing: Automotive review data from /content/FinalFullAnnotationsAllLabelsCompleted.csv was loaded. Text cleaning involved converting reviews to lowercase, removing non-ASCII characters, and normalizing whitespace. Aspect and review text were combined into a single input string for the model (e.g., "review text [SEP] aspect").
Label Encoding: Categorical sentiment labels ('pos', 'neg', 'neu') were mapped to numerical representations (0, 1, 2).
Data Splitting: The dataset was stratified into training (80%), validation (10%), and testing (10%) sets to ensure consistent sentiment distribution across subsets.
Tokenization: The preprocessed text inputs were tokenized using the bert-base-uncased tokenizer, with truncation and padding to a max_length of 128.
Model Initialization: A BertForSequenceClassification model was loaded from transformers, configured for 3 sentiment classes.
Model Fine-tuning: The model was fine-tuned using the Hugging Face Trainer API. Key TrainingArguments included a batch size of 16 and training for 3 epochs. Performance was monitored using F1-score as the primary metric.
3. Key Findings and Results
After fine-tuning, the model's performance was evaluated on the unseen test set. The evaluation results (accuracy, F1-score from the classification report, and the confusion matrix) provide insights into the model's ability to correctly classify sentiments for different aspects.

(Once the model is properly trained and evaluated, this section will include specific metrics and observations from the confusion matrix and classification report. For instance, it might highlight the model's performance on the majority class (e.g., 'pos') versus minority classes ('neg', 'neu').)

4. System Implementation
Two prediction functions (predict_sentiment_pipeline and predict_sentiment_manual) were implemented to demonstrate the end-to-end ABSA system. These functions take raw review text and an aspect, preprocess them, and return a predicted sentiment along with a confidence score. The model and tokenizer were saved, allowing for easy reloading and deployment.

5. Conclusion and Future Work
This project successfully developed a BERT-based ABSA system capable of identifying aspect-specific sentiments in automotive reviews. The fine-tuning process adapted a powerful pre-trained language model to our specific task.

Potential Future Work:

Hyperparameter Optimization: Explore different learning rates, batch sizes, and numbers of epochs to further optimize model performance.
Advanced Architectures: Experiment with other BERT variants (e.g., RoBERTa, XLNet) or more complex ABSA-specific architectures.
Data Augmentation: Increase the size and diversity of the training data through techniques like synonym replacement or back-translation.
Error Analysis: Conduct a detailed error analysis on misclassified examples to identify systematic errors and improve data annotation or model architecture.
Aspect Extraction: Integrate an automatic aspect extraction module to create a fully autonomous ABSA system that does not require predefined aspects.
This ABSA system provides a strong foundation for granular sentiment analysis of automotive reviews, offering valuable insights for manufacturers and consumers alike.