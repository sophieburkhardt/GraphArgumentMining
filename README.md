# Thesis
Focusing knowledge-based graph argument mining via topic modeling

# Requirements
Python 3.6 for the classifier, run
```
py -3.6 -m pip -r install requirements_3.6.txt
```
Python 3.7+ for the evidence extraction, run
```
py -3.7 -m pip -r install requirements_3.7+.txt
```

# Data
Download from [mail to patrick@abels-family.de] and extract as `data` folder into the `project` folder.
Download from [mail to patrick@abels-family.de] and extract as `embeddings` folder into the `wikidata-access` folder.

# Training and testing
Run the following in the `project` folder to generate the data:
```
python run.py \
--topic "school_uniforms"\
--num_cases 200 \
--depth 10 \
--include_lda True \
--include_wordvec True \
--par_query True \
--include_openie True
```
Run the following in the main folder to fill the classifier with the data:
```
move project\results\* wikidata-access\results\UKPSententialArgMin\knowledge_graph\wikidata_no_paths
```
Run the following in the `wikidata-access` folder to execute the classifier on the data:
```
py -3.6 generate_data_and_train.py \
--config configs/model_configs/UKPSententialArgMin/knowledge_graph/KBiLSTM_UKP_wikidata.json \
--predict-test 1
```