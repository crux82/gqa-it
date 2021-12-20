# GQA-it
## Italian Question Answering on Image Scene Graphs

GQA-it is a **large-scale Italian dataset for Visual Question Answering** based on the balanced version of [GQA](https://cs.stanford.edu/people/dorarad/gqa/about.html).

GQA-it contains more than **1 million question/answer pairs in Italian over 80K images** obtained by applying Neural Machine Translation. 

Most importantly, a **Test set of 3,000 question-answer pairs has been manually validated to provide a valuable benchmark in Italian**.

GQA-it has been used to adapt to Italian the [LXMERT](https://github.com/airsplay/lxmert) state-of-the-art VQA neural architecture, and the resuts have shown comparable results between English and Italian models. More details about GQA-it can be found in the original paper [Croce et al. 2021](http://ceur-ws.org/Vol-3033/paper42.pdf).


This repository is organized as follows:

* `train.json.gz` is a compressed version of the json training file. It contains training examples derived from the original GQA trainig material (balanced version) available at the following [LINK](https://nlp.cs.unc.edu/data/lxmert_data/gqa/train.json).
* `valid.json.gz` is a compressed version of the json development file derived from the original GQA validation material (balanced version) available at the following [LINK](https://nlp.cs.unc.edu/data/lxmert_data/gqa/valid.json).
* `testdev.json.gz` is a compressed version of the json test/dev file derived from the original GQA test/validation material (balanced version) available at the following [LINK](https://nlp.cs.unc.edu/data/lxmert_data/gqa/testdev.json). This file is called `testdev` and not `test` since it does not reflect the official and complete English test material, which is not publicly available; however, this smaller dataset is defined to be representative of the entire test set and it is traditionally used to evaluate VQA systems. 
* `testdev3k_validated.json.gz` is a compressed file containing  3000 manually validated test/benchmarking examples derived from the origial `testdev.json.gz`. 
* `trainval_label2ans.json.gz` and `trainval_ans2label.json.gz` reflect the set of possible answers and they are required by LXMERT (that models the VQA process as a classification task).  

Please notice that the above files can be directly used to train an LXMERT model, as they are correspondingly formatted; please refer to the following [LINK](https://github.com/airsplay/lxmert#gqa). Most importantly each question/answer pair refers to the ID of the original image from the GQA dataset, so that you can downdload the correspoding [visual data](https://cs.stanford.edu/people/dorarad/gqa/download.html) or you can directly use the feature vector linked [HERE](https://github.com/airsplay/lxmert#gqa).


### How to cite GQA-it

If you find GQA-it useful for your research, please cite the following paper:

~~~~
@inproceedings{DBLP:conf/clic-it/CrocePL021,
  author    = {Danilo Croce and
               Lucia C. Passaro and
               Alessandro Lenci and
               Roberto Basili},
  editor    = {Elisabetta Fersini and
               Marco Passarotti and
               Viviana Patti},
  title     = {GQA-it: Italian Question Answering on Image Scene Graphs},
  booktitle = {Proceedings of the Eighth Italian Conference on Computational Linguistics,
               CLiC-it 2021, Milan, Italy, January 26-28, 2022},
  series    = {{CEUR} Workshop Proceedings},
  volume    = {3033},
  publisher = {CEUR-WS.org},
  year      = {2021},
  url       = {http://ceur-ws.org/Vol-3033/paper42.pdf},
  timestamp = {Wed, 15 Dec 2021 17:49:17 +0100},
  biburl    = {https://dblp.org/rec/conf/clic-it/CrocePL021.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
~~~~


## Download

To download the GQA-it dataset, please refer to [https://github.com/crux82/gqa-it](https://github.com/crux82/gqa-it)

The resource is a joint project developed by the [Semantic Analytics Group](http://sag.art.uniroma2.it) of
the [University of Roma Tor Vergata](http://web.uniroma2.it/home) and the [CoLing Lab](https://colinglab.fileli.unipi.it) of the [University of Pisa](https://www.unipi.it). 
You can download a copy of the dataset (distributed under the CC BY-SA 4.0 license).

## Size of GQA-it

The GQA-it dataset contains the following elements:

| Dataset | Images | Question/Answer Pairs |
| -------------- | --------------: | --------------: |
| train  | 72,140 | 943,000 |
| valid  | 10,234 | 132,062 |
| test-dev (silver) | 398 |12,578 |
| test-dev (gold) | 398 | 3,000 |
				

## Evaluating a Neural Visual Question Answer System over GQA-it

The [LXMERT](https://github.com/airsplay/lxmert) VQA neural system [Tan and Bansal, 2019] was adapted to the Italian language. The system was trained on the automatically translated version of GQA [Hudson and Manning, 2019] in order to measure the performance of a state-of-the-art model on the GQA-it dataset. The reported results are obtained on a manually-validated Test Set odf 3,000 question-answer pairs (gold) and on the automatically translated resource (silver).
More details and comparative results are described in [Croce et al. 2021]. 


| | Accuracy |
| --- | :---: |
|Results over the Test  Set (gold) | 51.0 % |
|Results over the Test  Set (silver) | 52.6 % |


## Example
![](img/n90294.jpg)

| Language | Question | Answer |
| --- | :---: | :---: |
| En | Is the remote to the right or to the left of the book? | right |
| It | _Il telecomando è a destra o a sinistra del libro?_ | _destra_ |
| En | How thick is the book to the left of the remote? | thick | 
| It | _Quanto è spesso il libro a sinistra del telecomando?_ | _spesso_ |
| En | What device is to the left of the calculator made of plastic?| charger |
| It | _Quale dispositivo si trova a sinistra della calcolatrice di plastica?_ | _caricabatterie_ |
| En | What's the charger made of? | plastic |
| It | _Di cosa è fatto il caricabatterie?_ | _plastica_ |
| En | Are there any phones? | no |
| It | _Ci sono dei telefoni?_ | _no_ |


  
## References

[Hudson and Manning, 2019] Hudson, D. A., & Manning, C. D. (2019). Gqa: A new dataset for real-world visual reasoning and compositional question answering. In Proceedings of the IEEE/CVF conference on computer vision and pattern recognition (pp. 6700-6709).

[Tan and Bansal, 2019] Tan, H., & Bansal, M. (2019). Lxmert: Learning cross-modality encoder representations from transformers. arXiv preprint arXiv:1908.07490.

[Croce et al. 2021] Croce, D., Passaro, L. C., Lenci, A., & Basili, R. (2021). GQA-it: Italian Question Answering on Image Scene Graphs.

## Contacts

For any questions or suggestions, you can send an e-mail to <croce@info.uniroma2.it>
