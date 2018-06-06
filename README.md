# topic_modelling_mallet
Labeled LDA topic modelling with MALLET in python
<br/>
This software is an application of a bunch of python libraries for LDA and LabeledLDA with Gensim and MALLET.
<br/>
For the LLDA, you need to have MALLET (either 7 or 8) installed and pass the results to the MALLET executable. The repo also includes a script to prepare your data for MALLET, on the basis of TEI files (in our case tagged with [Alix Tagger](https://github.com/ANRChapitres/tagging)).<br/>
## Once you have made your files ready for MALLET, two cases :<br/>
### Using Mallet 2.0.7 (easier for data use in python script), from your mallet installation directory :<br/>
  - if you want to do simple LDA, do this in your terminal : <br/>
```bin/mallet import-dir --input your/path/to/your/txt/files/ --output /tmp/topic-input-doc.mallet --keep-sequence --stoplist-file your/path/to/your/stopword_file.txt
bin/mallet train-topics --input /tmp/topic-input-DOC.mallet --num-topics 20 --output-doc-topics /tmp/doc-topics-doc.txt --output-topic-keys /tmp/topic-keys-doc.txt --random-seed 1
```
<br/>
### Using Mallet 2.0.8 (the older version does not contain the LabeledLDA function), from your mallet installation directory (after having used the preprocessing script putting all files into one and having decided the labels you wanted):<br/>
```bin/mallet import-file --input doc.txt --output doc.seq --stoplist-file stopwords.txt --label-as-features --keep-sequence --line-regex '([^\t]+)\t([^\t]+)\t(.*)'<br/>
```bin/mallet run cc.mallet.topics.LabeledLDA --input doc.seq --output-topic-keys doc-llda.keys --output-doc-topics doc-llda-doc-topics.txt --random-seed 1
```
<br/>
Once you have run this, put either the topic-keys-doc.txt (for LDA) or the doc-llda-doc-topics.txt (for LLDA) in the LDA or the LLDA ipynb scripts.


  
  
