## Environment Setup
```
conda create --name Whisper-Finetune python=3.8.5
conda activate Whisper-Finetune
#pip install torch==1.13.1+cu116 torchvision==0.14.1+cu116 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu116
pip install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu117
python -m pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install -U huggingface_hub
```
