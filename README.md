# ConCat

## Basic Usage

### Environment

```shell
# create virtual environment
conda create --name xj_concat python=3.7
# activate environment
conda activate xj_concat
# install pytorch==1.12.0
conda install pytorch==1.12.0 torchvision==0.13.0 torchaudio==0.12.0 cudatoolkit=11.3 -c pytorch
# install other requirements
pip install -r requirements.txt
```

## Prepare Data
Datasets download link: [Google Drive](https://drive.google.com/file/d/1o4KAZs19fl4Qa5LUtdnmNy57gHa15AF-/view?usp=sharing) or [Baidu Drive (password: `1msd`)](https://pan.baidu.com/s/1tWcEefxoRHj002F0s9BCTQ).
The datasets we used in the paper are come from:
- [Weibo](https://github.com/CaoQi92/DeepHawkes) (Cao *et al.*, [DeepHawkes: Bridging the Gap between 
Prediction and Understanding of Information Cascades](https://dl.acm.org/doi/10.1145/3132847.3132973), CIKM, 2017). You can also download Weibo dataset [here](https://drive.google.com/file/d/1fgkLeFRYQDQOKPujsmn61sGbJt6PaERF/view?usp=sharing) in Google Drive.  
- [APS](https://journals.aps.org/datasets) (Released by *American Physical Society*, obtained at Jan 17, 2019).  

Put the dataset.txt file into "data/aps/" or "data/weibo/" directory

### Run the code
```shell
#Run at the root of this repo:
python setup.py build_ext --inplace
# generate information cascades
python gen_cas.py --data=data/weibo/ --observation_time=1800 --prediction_time=86400
# generate cascade graph
python gen_emb.py --data=data/weibo/ --observation_time=1800 --max_seq=100
#train
python train.py --data=data/weibo/ --observation_time=1800 --max_seq=100

```
More running options are described in the bash file: "train.sh"




