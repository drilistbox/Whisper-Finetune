## quick test for BELLE-2/Belle-distilwhisper-large-v2-zh or BELLE-2/Belle-whisper-large-v2-zh
step 1. Install environment for pytorch training
```bash
conda activate Whisper-Finetune
audio_path=/data01/home/shuchangyong/projects/big_model/whisper-pyannote/test_16000/demo/Hi0Fp_nZSZ0.wav
model_name=BELLE-2/Belle-distilwhisper-large-v2-zh
model_name=BELLE-2/Belle-whisper-large-v2-zh
```

step 2. 下载模型
```bash
rm -r models/${model_name}
mkdir -p models/${model_name}
export HF_ENDPOINT=https://hf-mirror.com
pc huggingface-cli download --resume-download --local-dir-use-symlinks False ${model_name} --local-dir models/${model_name}
```

step 3. 转换模型
```bash
ct2-transformers-converter --model models/${model_name}/ --output_dir models/${model_name}-ct2_model
```

step 4. 模型推理
```python
pc python infer_ct2.py --audio_path=${audio_path} --model_path=models/${model_name}-ct2_model --local_files_only True --vad_filter True
```

## quick test for fast_whisper
model_mode can be referred from follows:

```python
_MODELS = {
    "tiny.en": "Systran/faster-whisper-tiny.en",
    "tiny": "Systran/faster-whisper-tiny",
    "base.en": "Systran/faster-whisper-base.en",
    "base": "Systran/faster-whisper-base",
    "small.en": "Systran/faster-whisper-small.en",
    "small": "Systran/faster-whisper-small",
    "medium.en": "Systran/faster-whisper-medium.en",
    "medium": "Systran/faster-whisper-medium",
    "large-v1": "Systran/faster-whisper-large-v1",
    "large-v2": "Systran/faster-whisper-large-v2",
    "large-v3": "Systran/faster-whisper-large-v3",
    "large": "Systran/faster-whisper-large-v3",
    "large-v2-zh": "BELLE-2/Belle-whisper-large-v2-zh",
}
```

cmd

```bash
model_mode=tiny.en
model_mode=tiny
model_mode=base.en
model_mode=base
model_mode=small.en
model_mode=small
model_mode=medium.en
model_mode=medium
model_mode=large-v1
model_mode=large-v2
model_mode=large-v3
model_mode=large

audio_path=/data01/home/shuchangyong/projects/big_model/whisper-pyannote/test_16000/demo/Hi0Fp_nZSZ0.wav
model_mode=large-v2
pc python infer_ct2.py --audio_path=${audio_path} --model_path=${model_mode} --local_files_only False --vad_filter True
```
