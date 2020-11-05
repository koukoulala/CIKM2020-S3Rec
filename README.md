
Code for our CIKM 2020 Paper ["**S3-Rec: Self-Supervised Learning for Sequential
 Recommendation with Mutual Information Maximization"**](https://arxiv.org/pdf/2008.07873.pdf)

## Overview
![avatar](model.PNG)

## Results
Performance comparison of different methods on six datasets. The best performance and the second best performance
methods are denoted in bold and underlined fonts respectively.

In the PAPER, we pair the ground-truth item 
with **99 randomly sampled negative items** that the user
has not interacted with, and report the results of 
HR@{1, 5, 10}, NDCG@{5, 10} and MRR. The used test files are name as 
```
data_name_neg.txt
```
The results are shown in the following pic.
![avatar](sample_99.PNG)


In the repo, we rank the ground-truth item with **ALL the items**.
We omit the FM and AutoInt because they need 
enumerate all user-item pairs, which take a very long time. 
The results are shown in the following pic.


![avatar](all_rank.PNG)

### requirements
```shell script
pip install -r requirements.txt
```

## data preprocess
```shell script
./data/data_process.py

data-name.txt
one user per line
user_1 item_1 item_2 ...
user_2 item_1 item_2 ...

data-name_item2attributes.json
{item_1:[attr, ...], item_2:[attr, ...], ... }
```

## pretrain
```shell script
python run_pretrain.py \
--data_name Beauty
```

## finetune
```shell script
python run_finetune.py \
--data_name Beauty \
--ckp 100
```


### Cite
If you find the our codes and datasets useful for your research or development, please cite our paper:

```
@inproceedings{DBLP:conf/cikm/ZhouWZZWZWW20,
  author    = {Kun Zhou and
               Hui Wang and
               Wayne Xin Zhao and
               Yutao Zhu and
               Sirui Wang and
               Fuzheng Zhang and
               Zhongyuan Wang and
               Ji{-}Rong Wen},
  editor    = {Mathieu d'Aquin and
               Stefan Dietze and
               Claudia Hauff and
               Edward Curry and
               Philippe Cudr{\'{e}}{-}Mauroux},
  title     = {S3-Rec: Self-Supervised Learning for Sequential Recommendation with
               Mutual Information Maximization},
  booktitle = {{CIKM} '20: The 29th {ACM} International Conference on Information
               and Knowledge Management, Virtual Event, Ireland, October 19-23, 2020},
  pages     = {1893--1902},
  publisher = {{ACM}},
  year      = {2020},
  url       = {https://doi.org/10.1145/3340531.3411954},
  doi       = {10.1145/3340531.3411954},
  timestamp = {Mon, 19 Oct 2020 18:49:47 +0200},
  biburl    = {https://dblp.org/rec/conf/cikm/ZhouWZZWZWW20.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

### Contact
If you have any question for our paper or codes, please send email to hui.wang@ruc.edu.cn.