# Differential diagnosis with bidirectional LSTM

The algorithm can classify 10 common medical conditions based on the presenting history and physical examination performed on the patient. The algorithm can also identify "culprits" for the decision it made, i.e. specific words in the input string that contributes most to the prediction. 

## Conditions
1. Acromeglay
2. Addison's disease
3. Aplastic anemia
4. Asthma
5. Gout
6. Graves' disease
7. Nephrolithiasis
8. Systemic sclerosis
9. Ulcerative colitis
10. Urticaria

## Data
Training data (symptoms, history and physical examination) was collected from multiple websites, including Mayo Clinic and Medscape. Testing data was collected from Wikipedia and NHS website. 

## Model
A bidirectional LSTM was used for the model.

## Explainable AI
A "glass-box" mode was introduced in the algorithm that explains its decision (a pun referring to the fact that medical AI are commonly considered as "black-box"). To identify the words that increases the output probability of the model's prediction the most, a forward run was first performed to indentify the model's prediction. Then, the probability changes for each word was tracked and the words that resulted in greatest increases were recorded. 

## Results
![Capture](https://user-images.githubusercontent.com/44185972/80285503-0e98fb00-8758-11ea-80a3-8b74d3728a1d.PNG)

A top 1 accuracy of 0.9 and top 2 accuracy of 1.0 was achieved with testing. In this example, the ground truth condition is systemic sclerosis, in which the model predicted correctly. Systemic scleroris is a condition that causes hardening of the skin and internal organs. The algorithm correctly indentifies (in "culprits") that "shortness of breath", "lung impairment" and "reddish" (referring to reddish skin) were the most important words resulting in its prediction.

Also note that the condition with the second highest probability was urticaria. This is reasonable as urticaria is a skin condition, which has many overlapping symptoms with systemic scleroris. 
