# Word embeddings capture latent knowledge discovery
Inspired by [this application](https://github.com/materialsintelligence/mat2vec)

# Setup
```
#create venv
python3 -m venv venv
#activate venv
source venv/bin/activate
#install requirements
pip3 install --ignore-installed -r requirements.txt
```

# Run crawler
```
mkdir results
python3 crawler.py
```

# Merge abstract files
This will generate `results_file.txt` 
```
cd bert
python3 merge_txt.py 
```

# Word embeddings

## Word2Vec
Training the model
```
cd word2vec
python3 train.py
```
Loading the model
```
from gensim.models import Word2Vec
model = Word2Vec.load('model.bin')
```
Access vector for one word
```
model['cytarabin']
```

## GloVe
```
git clone http://github.com/stanfordnlp/glove
cd glove && make
```
Making changes to `demo.sh`:
- Remove the script from if to fi after 'make'
- Replace the CORPUS name with `"../results_file.txt"`
- On `if [ "$CORPUS" = 'text8' ]; then` replace `text8` with `"../results_file.txt"`

Training the model
```./demo.sh```

Word vectors will be placed on `vectors.txt` 

## BERT
Train tokenizer
```
cd bert
python3 train_tokenizer.py
```

Train from scratch
```
python3 from_scratch.py
```




