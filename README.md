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
model_a4.add_adapter("JY031/gemma2-2b-yoda-rlvr", adapter_name="rlvr")
model_b3 = model_a4

```
