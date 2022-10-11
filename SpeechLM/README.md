# SpeechLM

<!--**Pre-trained models for speech related tasks**-->

 [**SpeechLM**](https://arxiv.org/abs/2209.15329): **Enhanced Speech Pre-Training with Unpaired Textual Data**


- The code and checkpoints will be released here.
- Oct 2022: release preprint in [arXiv](https://arxiv.org/abs/2209.15329)
- (Scheduled) Oct 2022: release the code and models

## Setup
```
git submodule update --init SpeechLM/fairseq
cd SpeechLM/
pip install --editable fairseq/
pip install sacrebleu==1.5.1
```

## Data Preparation
> We put examples in [dataset](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset)

### Pre-training data
- **Unlabeled speech:** please follow the steps of wav2vec 2.0 manifest [here](https://github.com/pytorch/fairseq/tree/main/examples/wav2vec#prepare-training-data-manifest) to prepare [`train.tsv`](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset/LibriSpeech/phone_unit/train_sample100.tsv)
- **Phoneme units for speech:** use phoneme-unit tokenizer to process the speech to prepare [`train.phn`](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset/LibriSpeech/phone_unit/train_sample100.phn)
- **Hidden units for speech:** use hidden-unit tokenizer to process the speech to prepare [`train.km`](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset/LibriSpeech/hidden_unit/train_sample100.km)
> The hidden-unit tokenizer used in this word is [a K-means model on the top of the Hubert Base model](https://github.com/facebookresearch/fairseq/tree/main/examples/hubert/simple_kmeans).
- Create dict for the target units [`dict.phn.txt`](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset/LibriSpeech/phone_unit/dict.phn.txt) or [`dict.km.txt`](https://github.com/microsoft/SpeechT5/tree/main/SpeechLM/dataset/LibriSpeech/hidden_unit/dict.km.txt)

- **Unpaired Text:** convert [LibriSpeech LM corpus](http://www.openslr.org/11/) to normalized charecters to get `librilm.phn-ltr.ltr` and `dict.ltr.txt`.
- **Phoneme tokens for text:** use the lexicon provided by LibriSpeech LM corpus to convert words to phonemes, then apply up-sampling to get `librilm.phn-ltr.phn`.
- **Phoneme tokens for text:** use the text-to-unit tokenizer to convert phonemes to units to get `librilm.phn-ltr.phn`.

### ASR data for LibriSpeech
- Please follow the steps of wav2vec 2.0 manifest [here](https://github.com/pytorch/fairseq/tree/main/examples/wav2vec#prepare-training-data-manifest) to prepare `train.tsv` and `train.ltr`.

### ST data for CovoST-2 En-XX
- Please follow the scripts below to prepare the required files
```

```