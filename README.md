# AI Customer Complaint Analyzer

This deep learning model was built to analyse a "complaint dataset" and predict the following 3 things:

• The primary category of complaint 
• The specific issue type  
• The urgency/severity of the complaint (1–5)  

The need was to build a system that can:

- Understand complaint context  
- Identify root issues  
- Flag high-risk cases quickly  

---

# Approach

I framed the problem as **multi-task NLP classification**.

Instead of training separate models, I used a single Transformer encoder with three prediction heads:

• Primary category classifier  
• Secondary issue classifier  
• Severity predictor  

This allows the model to share language understanding across tasks.

---

# Models Used

I experimented with several Transformer models and found the best performance using:

- DeBERTa-v3-base  
- RoBERTa-base  

Both models were fine-tuned on the complaint dataset.

Final predictions were made using an **ensemble of both models**, which improved stability and accuracy.

---

# Key Techniques

### Multi-Task Learning
One encoder, multiple tasks → better shared representations.

### Class-Weighted Loss
Handled class imbalance in complaint categories.

### Cross Validation
5-fold CV improved generalization.

### Model Ensembling
Averaging predictions from different architectures boosted performance.

---

# Final Performance

Final Score: **0.74835**

Evaluation metric:

0.3 × Primary Accuracy  
0.4 × Secondary Accuracy  
0.3 × Severity R²  

Secondary classification had the highest impact on score.

