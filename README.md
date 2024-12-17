# babylm
 
### Steps Taken to Recreate the Baseline (reproduced the [babyllama-10m-2024](https://huggingface.co/babylm/babyllama-10m-2024))

1. **Model configuration:**  
   Copied the existing model configuration.

2. **Tokenizer import:**  
   Imported the tokenizer associated with the model.

3. **Dataset preparation:**  
   Loaded both the training and development datasets.

4. **Data chunking:**  
   Split both the training and development datasets into chunks of 256 tokens each.

5. **Training arguments:**  
   Uploaded the specified training arguments.

6. **Tokenizer issue resolution:**  
   After the initial run, the tokenizer produced `None` values in the `input_ids` of the development set.  
   To fix this, I performed a  check and replaced all `None` values with `0`.

7. **Model training:**  
   Initiated the model training process.

   
| Model | BLiMP | BLiMP Supplement | 
| --- | --- | --- |
| TrainedModel | 66.56 | 55.52 |
| [BabyLlama](https://github.com/babylm/evaluation-pipeline-2024/blob/main/README.md#baselines) | 69.8| 59.5|


---

### Steps Taken to Create the Dummy Model

1. **Forward function override:**  
   Overwrote the model’s `forward()` function to return random logits.

2. **Model configuration:**  
   Reused the existing model configuration.

3. **Tokenizer import:**  
   Imported the same tokenizer as before.

4. **Sample sentence selection:**  
   Selected sample sentences that the [BabyLM Challenge](https://babylm.github.io/) [LM Evaluation Harness](https://github.com/EleutherAI/lm-evaluation-harness) uses.

5. **Testing randomness:**  
   Compared the dummy model (which produces random logits) to a non-trained model.  
   - **Dummy model:** On multiple runs, it returned random likelihoods, frequently changing which sentence it deemed “best.”  
   - **Untrained model:** Produced consistent values across runs, indicating stable but non-informative outputs.

| Model | BLiMP | BLiMP Supplement | 
| --- | --- | --- |
| DummyModel | 51.04 | 51.35 |

---
