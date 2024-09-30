# ACE-Process
A universal method to ACE process.

## Reference
- https://github.com/nlpcl-lab/ace2005-preprocessing
- https://github.com/LiXianyao/ace2005-preprocessing-With-Chinese-Branch-
- https://github.com/ll0ruc/ace2005chinese_preprocess

## Environment
- mac OS

## Prerequisites
1. Donwload ACE-Dataset from [here](https://catalog.ldc.upenn.edu/LDC2006T06)(This dataset is not free, you need to register and pay for it).
2. python environment with the following packages:
    - stanfordcorenlp 
    - beautifulsoup4 
    - nltk 
    - tqdm

you can install them by running the following command:
```
pip install stanfordcorenlp beautifulsoup4 nltk tqdm
```
4. if you don't have java environment, run:
```
brew install java
echo 'export PATH="/usr/local/opt/openjdk/bin:$PATH"' >> ~/.bash_profile
export CPPFLAGS="-I/usr/local/opt/openjdk/include"
source ~/.bash_profile
```
5. if you don't have wget, run:
```
brew install wget
```
6. Download stanford-corenlp model.
```
wget http://nlp.stanford.edu/software/stanford-corenlp-full-2018-10-05.zip
unzip stanford-corenlp-full-2018-10-05.zip

# and for Chinese
wget http://nlp.stanford.edu/software/stanford-chinese-corenlp-2018-10-05-models.jar
```

## Usage
```
# english
sudo python main.py --data=../ace_2005/data/English --nlp=./stanford-corenlp-full-2018-10-05

# chinese
sudo python main.py --data=../ace_2005/data/Chinese --nlp=./stanford-corenlp-full-2018-10-05
```

## Error:Resource punkt_tab not found.
Download URL: https://github.com/nltk/nltk_data
cd packages/tokenizers and download: punkt_tab.zip, punkt.zip
unzip both zip files in your directory.

## runtime error:
```
# set timeout more than 60000
with StanfordCoreNLP(args.host, memory='8g', timeout=60000, lang=args.lang, port=args.port) as nlp:
        # res = nlp.annotate('Donald John Trump is current president of the United States.', properties={'annotators': 'tokenize,ssplit,pos,lemma,parse'})
        # print(res)
        preprocessing('dev', dev_files, args.withValue, args.lang)
        preprocessing('test', test_files, args.withValue, args.lang)
        preprocessing('train', train_files, args.withValue, args.lang)
```
