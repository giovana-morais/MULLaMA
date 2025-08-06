<div>
  <h1>
    MU-LLaMA: <br>Music Understanding Large Language Model
  </h1>
</div>

[![PWC](https://img.shields.io/badge/%F0%9F%93%8E%20arXiv-Paper-red)](https://arxiv.org/abs/2308.11276)
[![PWC](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-MusicQA%20Dataset-green)]([https://arxiv.org/abs/2308.11276](https://huggingface.co/datasets/mu-llama/MusicQA))
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/music-understanding-llama-advancing-text-to/music-question-answering-on-musicqa-dataset)](https://paperswithcode.com/sota/music-question-answering-on-musicqa-dataset?p=music-understanding-llama-advancing-text-to)

This is an adaptation of the repository for *[Music Understanding LLaMA: Advancing Text-to-Music Generation with Question Answering and Captioning](https://arxiv.org/abs/2308.11276)*

The demo page with more information regarding the MU-LLaMA model is avilable [here](https://crypto-code.github.io/MU-LLaMA-Demo/).

## Introduction
The MU-LLaMA model is Music Understanding Language Model designed with the purpose of answering questions based on music. Our model is also designed with the purpose of captioning music files to generate Text-to-Music Generation datasets. The model uses MERT + LLaMA as the backbone and employs an adapter to encoperate music context information to guide LLaMA's output. MERT was chosen as the music encoder for our model after comparison of different music representation models, which can be viewed [here](https://github.com/crypto-code/Music-Representation-Comparison). We also provide the code for generating our MusicQA dataset from [MusicCaps](https://www.kaggle.com/datasets/googleai/musiccaps) and the [MagnaTagATune](https://mirg.city.ac.uk/codeapps/the-magnatagatune-dataset) datasets.

## MU-LLaMA Demo

For the working of our model, Facebook's LLaMA-2 model weights are required, details on obtaining these weights are given on [HuggingFace](https://huggingface.co/docs/transformers/main/model_doc/llama). Our pretrained weights for the MU-LLaMA model, finetuned from **LLaMA 7B-2** can be downloaded [here](https://huggingface.co/mu-llama/MU-LLaMA/tree/main). Once downloaded, store the files in the ckpts folder within the MU-LLaMA directory.

Once downloaded the directory structure will be as shown below.
```
.
├── ...
├── MU-LLaMA
│   ├── ckpts
│   │   │── LLaMA
│   │   │   │── 7B
│   │   │   │   │── checklist.chk
│   │   │   │   │── consolidated.00.pth
│   │   │   │   │── params.json
│   │   │   │── llama.sh
│   │   │   │── tokenizer.model
│   │   │   │── tokenizer_checklist.chk
│   │   │── 7B.pth
│   │   ├── checkpoint.pth
└── ...
```

We use Python 3.9.17 for this project and the library requirements are given in [***requirements.txt***](./requirements.txt). The demo can be run using [***gradio_app.py***](./MU-LLaMA/gradio_app.py).
```
python gradio_app.py --model ./ckpts/checkpoint.pth --llama_dir ./ckpts/LLaMA
```

## Training MU-LLaMA

To train the MU-LLaMA model, follow the steps as below.

### MU-LLaMA Inference

To test the model without Gradio, the [***inference.py***](./MU-LLaMA/inference.py) script can be used.
```
usage: inference.py [-h] [--model MODEL] [--llama_type LLAMA_TYPE] [--llama_dir LLAMA_DIR] [--mert_path MERT_PATH] --audio_path AUDIO_PATH [--question QUESTION]

optional arguments:
  -h, --help            show this help message and exit
  --model MODEL         Name of or path to the trained checkpoint
  --llama_type LLAMA_TYPE
                        Type of llama original weight
  --llama_dir LLAMA_DIR
                        Path to LLaMA pretrained checkpoint
  --mert_path MERT_PATH
                        Path to MERT pretrained checkpoint
  --audio_path AUDIO_PATH
                        Path to the input music file
  --question QUESTION   Question to ask the model
```

## Acknowledgements

This code contains elements from the following repos:
- [OpenGVLab/LLaMA-Adapter](https://github.com/OpenGVLab/LLaMA-Adapter)
- [yizhilll/MERT](https://github.com/yizhilll/MERT)


## Cite our work
If you find this repo useful, please consider citing:
```bibtex
@article{liu2023music,
  title={{Music Understanding LLaMA: Advancing Text-to-Music Generation with Question Answering and Captioning}},
  author={Liu, Shansong and Hussain, Atin Sakkeer and Sun, Chenshuo and Shan, Ying},
  journal={arXiv preprint arXiv:2308.11276},
  year={2023}
}
```
