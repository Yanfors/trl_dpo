# trl_dpo

## Quick Start

### sft

```bash
accelerate launch ./sft_llama2.py \
    --output_dir="./sft_tinyllama" \
    --max_steps=500 \
    --logging_steps=10 \
    --save_steps=10 \
    --per_device_train_batch_size=4 \
    --per_device_eval_batch_size=1 \
    --gradient_accumulation_steps=2 \
    --gradient_checkpointing=False \
    --group_by_length=False \
    --learning_rate=1e-4 \
    --lr_scheduler_type="cosine" \
    --warmup_steps=100 \
    --weight_decay=0.05 \
    --optim="paged_adamw_32bit" \
    --bf16=True \
    --remove_unused_columns=False \
    --run_name="sft_llama2" \
    --report_to="wandb"
```

### dpo
```bash
accelerate launch ./dpo_llama2.py \
    --model_name_or_path="sft_tinyllama/final_checkpoint" \
    --output_dir="dpo"
```
