# comp0264_cw_group11
A repo storing coursewk of UCL comp0264 year 2526 group 11

# Note

1. model in A2 is pushed to
[https://huggingface.co/chubao/gemma2-2b-yoda](https://huggingface.co/chubao/gemma2-2b-yoda)

2. model in A4 is pushed to
[https://huggingface.co/chubao/gemma2-2b-yoda-a4](https://huggingface.co/chubao/gemma2-2b-yoda-a4)

3. model in B3 is in pushed to
[https://huggingface.co/JY031/gemma2-2b-yoda-rlvr](https://huggingface.co/JY031/gemma2-2b-yoda-rlvr)

4. you could load the model from huggingface by:
```python
tokenizer = AutoTokenizer.from_pretrained("chubao/gemma2-2b-yoda-a4")
# Step 1: load base model
base = AutoModelForCausalLM.from_pretrained(MODEL_ID, **model_kwargs)

# Step 2: overlay the adapter from hub
model_a4 = PeftModel.from_pretrained(base, "chubao/gemma2-2b-yoda-a4").eval()

#Step 3: overlay the adapter for model_b3 from hub
model_a4.load_adapter("JY031/gemma2-2b-yoda-rlvr", adapter_name="rlvr")
model_b3 = model_a4

```

## Local Model Weights (Google Drive)

Due to GitHub file size limits, specific trained adapter weights are hosted on Google Drive. To run the evaluation notebooks locally, download the contents of the following folders and place them directly into the `models/` directory.

### 1. RLVR Balanced Model
* **Download Link:** [Google Drive Link 1](https://drive.google.com/drive/folders/1pmsCHzJ4DuGj2L-uVgDtMLeLHrRSqRls?usp=sharing)
* **Target Folder:** `models/gemma2-2b-yoda-8bit-full-rlvr-balanced/`

### 2. RLVR Balanced Model (Fixed)
* **Download Link:** [Google Drive Link 2](https://drive.google.com/drive/folders/1yISuwa1Qo-g_mt7kIXjGCPkHB3byrORj?usp=sharing)
* **Target Folder:** `models/gemma2-2b-yoda-8bit-full-rlvr-balanced-FIXED/`

### Expected Directory Structure
Ensure your local structure matches this before running the notebooks:
```text
COMP0264_CW_GROUP11/
├── models/
│   ├── gemma2-2b-yoda-8bit-full-rlvr-balanced/
│   ├── gemma2-2b-yoda-8bit-full-rlvr-balanced-FIXED/
│   ├── gemma2-2b-yoda-q4-rlvr/
│   └── .gitkeep
├── datasets/
├── plots/
├── yoda_style_classifier/
...
```
