# Results & Evaluation

## 1. Overview of Baseline Models

Two different recurrent architectures were initially explored for tweet sentiment classification. The first model used an LSTM-based approach, which consisted of an embedding layer, an LSTM layer, a dropout layer to reduce overfitting, and a dense output layer with sigmoid activation. This model demonstrated moderate performance but showed some imbalance between the negative and positive classes.

The second model employed a GRU-based approach, replacing the LSTM layer with a GRU layer while keeping a similar overall architecture. The GRU model delivered slightly more balanced predictions across both classes, which motivated further exploration using this architecture.

**Observation:**  
The GRU-based model provided more consistent performance across both negative and positive tweets, making it the preferred candidate for further refinement.

---

## 2. Hyperparameter Tuning of the GRU Model

To enhance performance, the GRU model underwent hyperparameter tuning using a Hyperband algorithm. The tuning process focused on key parameters, including:
- The number of units in the GRU layer
- The dropout rate to help control overfitting
- The learning rate for the optimizer

After an extensive search through various configurations, an optimal set of hyperparameters was identified that improved the model's validation performance and achieved more balanced predictions across classes. Although the final test performance was slightly lower than the best validation performance—a common occurrence in real-world scenarios—the tuned model showed good and consistent results.

---

## 3. Final Model Construction and Evaluation

Based on the optimal hyperparameters from the tuning phase, the final GRU-based model was constructed. Its architecture includes:
- **Embedding Layer:** Converts each token into a dense vector representation.
- **GRU Layer:** Utilizes the tuned number of units to capture sequential context.
- **Dropout Layer:** Applies a dropout rate to reduce overfitting.
- **Dense Output Layer:** Uses a sigmoid activation for binary classification.

The model was compiled with an appropriate optimizer and trained using early stopping to ensure that the best-performing weights were retained. A portion of the training data was set aside for validation. When evaluated on the test set, the final model exhibited strong performance with balanced predictive ability across both negative and positive sentiments.

**Performance Summary:**  
- The model achieved solid overall accuracy and a low loss on the test data.
- The classification metrics (precision, recall, and F1-scores) were well-balanced for both classes.
- Analysis via a confusion matrix confirmed that most tweets were correctly classified, with only a few misclassifications in cases of ambiguous or nuanced sentiment.

**Why the Results Aren't Higher:**  
Tweet sentiment analysis is inherently challenging due to the short, informal nature of tweets. They often contain slang, abbreviations, emojis, and sarcasm, which can obscure the underlying sentiment. This complexity means that even a well-tuned model may only achieve moderate performance.

---

## 4. Model Interpretation & Next Steps

**Model Interpretation and Error Analysis:**  
- Misclassified tweets should be reviewed to understand common error patterns, such as ambiguous language or sarcasm.
- Explainability techniques (for example, LIME or SHAP) can be applied to reveal which features drive the model’s decisions.

**Further Improvements:**  
- Additional regularization (like adjusting dropout rates or incorporating L2 regularization) may help mitigate overfitting.
- Refining the hyperparameter search or using data augmentation techniques could lead to incremental improvements.
- Exploring ensemble methods or integrating more advanced architectures (such as transformer-based models) might further enhance performance.

---

## Conclusion

The project evolved from evaluating baseline LSTM and GRU architectures to refining the GRU model through systematic hyperparameter tuning. Despite the inherent challenges of tweet sentiment analysis—owing to the brevity and informal nature of the text—the final model demonstrates reasonable and balanced performance. This comprehensive approach lays a solid foundation for further improvements and eventual deployment in real-world applications.
