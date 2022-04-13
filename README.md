## Under Implementing...

#  CDFSE_FastSpeech2
This repo contains code accompanying the paper "Content-Dependent Fine-Grained Speaker Embedding for Zero-Shot Speaker Adaptation in Text-to-Speech Synthesis", which is implemented based on [ming024/FastSpeech2](https://github.com/ming024/FastSpeech2) (much thanks!).

## [Samples](https://thuhcsi.github.io/interspeech2022-cdfse-tts/) | [Paper](https://arxiv.org/pdf/2204.00990.pdf)

## Usage

### 0. Dataset
 1. Mandarin: [AISHELL3](https://www.openslr.org/93/)

### 1. Environment setup
```bash
pip3 install -r requirements.txt
```

### Data pre-processing
Please refer to [ming024/FastSpeech2](https://github.com/ming024/FastSpeech2)  for more details.

First, run
```bash
python3 prepare_align.py config/AISHELL3/preprocess.yaml
```

Download TextGrid Files or use MFA to align the corpus, then put TextGrid Files in processed_data/AISHELL/TextGrid/. 

Finally, run the preprocessing script 
```bash
python3 preprocess.py config/AISHELL3/preprocess.yaml
```


### 3. Training
```bash
python3 train.py -p config/AISHELL3/preprocess.yaml -m config/AISHELL3/model.yaml -t config/AISHELL3/train.yaml 
```

### 4. Inference
For batch:
```bash
python3 synthesize.py --source synbatch_sample.txt --restore_step 500000 --mode batch -p config/AISHELL3/preprocess.yaml -m config/AISHELL3/model.yaml -t config/AISHELL3/train.yaml 
```
	
For single:
```bash
python3 synthesize.py --text "测试一下合成效果." --refspeech [REF_MEL_PATH.npy] --restore_step 500000 --mode single -p config/AISHELL3/preprocess.yaml -m config/AISHELL3/model.yaml -t config/AISHELL3/train.yaml 
```

	
