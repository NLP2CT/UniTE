# UniTE

This is the repository of UniTE: Unified Translation Evaluation, which is build on COMET.
Datasets can be found at COMET repository.

# Training or Inference

The `main` repository is for inference. To train your own UniTE model, you can switch to `training` branch.

# Usage

## modelscope (recommended)

Recently we've released the related checkpoints on [modelscope](https://www.modelscope.cn/home). We helped the development of the modelscope toolkit to support the usage of UniTE models. You can refer to the model cards of [UniTE-UP](https://www.modelscope.cn/models/damo/nlp_unite_up_translation_evaluation_English_large/summary) and [UniTE-MUP](https://www.modelscope.cn/models/damo/nlp_unite_mup_translation_evaluation_multilingual_large/summary) for more details.

To use those models on modelscope, first you need to install the modelscope repository (if you know Chinese well, you can follow this [link](https://www.modelscope.cn/docs/%E7%8E%AF%E5%A2%83%E5%AE%89%E8%A3%85) for more details):

```
conda create -n modelscope python=3.9
conda activate modelscope

pip install "modelscope[nlp]" -f https://modelscope.oss-cn-beijing.aliyuncs.com/releases/repo.html
```

Then, you can refer to the given example codes on those two model cards.

## Github

1. Download this repository via git;
2. Download the checkpoints from [google drive](https://drive.google.com/file/d/1feqRHHRxcnw_CgLe6cofbe1qu_cBYLI_);
3. Extract the zip file, and you can get checkpoints ('ckpt' as suffix) and corresponding setting files ('yaml' files, totally three);
4. Run score.py to score the files you want:

```
Source-Only
python score.py -s src.txt -r ref.txt -t trans.txt --model model.ckpt --to_json results.src.json --hparams_file_path hparams.src.yaml

Reference-Only
python score.py -s src.txt -r ref.txt -t trans.txt --model model.ckpt --to_json results.ref.json --hparams_file_path hparams.ref.yaml

Source-Reference-Combined
python score.py -s src.txt -r ref.txt -t trans.txt --model model.ckpt --to_json results.src_ref.json --hparams_file_path hparams.src_ref.yaml
```

where:

- `src.txt` stores the source inputs
- `ref.txt` stores the target reference
- `trans.txt` stores the translation outputs (can also be named as candidates or hypotheses)
- `model.ckpt` is the path of model checkpoint
- `results.***.json` is the output path of json-formatted scores
- `hparams.***.yaml` is the path of setting file

# Citation

Please cite our paper if you find useful:

```

@inproceedings{wan2021robleurt,
    title = "{{RoBLEURT Submission for WMT2021 Metrics Task}}",
    author = "Wan, Yu  and
      Liu, Dayiheng  and
      Yang, Baosong  and
      Bi, Tianchi  and
      Zhang, Haibo  and
      Chen, Boxing  and
      Luo, Weihua  and
      Wong, Derek F.  and
      Chao, Lidia S.",
    booktitle = "Proceedings of the Sixth Conference on Machine Translation (WMT)",
    year = "2021",
}

@inproceedings{wan2022unite,
    title = "{{UniTE: Unified Translation Evaluation}}",
    author = "Wan, Yu  and
      Liu, Dayiheng  and
      Yang, Baosong  and
      Zhang, Haibo  and
      Chen, Boxing  and
      Wong, Derek F.  and
      Chao, Lidia S.",
    booktitle = "Annual Meeting of the Association for Computational Linguistics (ACL)",
    year = "2022",
}

@inproceedings{wan2022alibaba,
    title = "{{Alibaba-Translate China’s Submission for WMT 2022 Metrics Shared Task}}",
    author = "Wan, Yu  and
      Bao, Keqin  and
      Liu, Dayiheng  and
      Yang, Baosong  and
      Wong, Derek F.  and
      Chao, Lidia S.  and
      Lei, Wenqiang  and
      Xie, Jun",
    booktitle = "Proceedings of the Seventh Conference on Machine Translation (WMT)",
    year = "2022",
}

@inproceedings{bao2022alibaba,
    title = "{{Alibaba-Translate China’s Submission for WMT 2022 Quality Estimation Shared Task}}",
    author = "Bao, Keqin  and
      Wan, Yu  and
      Liu, Dayiheng  and
      Yang, Baosong  and
      Lei, Wenqiang  and
      He, Xiangnan  and
      Wong, Derek F. and
      Xie, Jun",
    booktitle = "Proceedings of the Seventh Conference on Machine Translation (WMT)",
    year = "2022",
}

```
