for mecab_process.pl

This script derives a new model based on an older model using the test and training files provided as described below. You can produce either a re-trained model or a lexical-addition-only model.

Usage: mecab_process.pl <RootDir> <OldModel> <NewModel> <'true' or 'false'>

where <RootDir> must contain two immediate subdirectories of the names <OldModel> and <NewModel>. the last argument indicates if you want a re-trained model.

Furthermore, each directory must contain the 'ingredients' as follows:

RootDir must contain four test sentence files for evaluation

<RootDir>--- test_sentences_kansai.txt
	  |- solutions_kansai.mecab
	  |- test_sentences_standard.txt
	  |- solutions_standard.mecab

where the first and the third are raw texts (kansai and standard), the second is the mecab-formatted gold standard (solution) of the first, and the fourth is that of the third. These files are constant for the whole process.

<RootDir>---<OldModel>--- model --- model_<OldModel>

OldModel dir must contain a subdirectory called model, which must then contain the old model files, including the binary called model_<OldModel>. This is the model you start from.

NewModel dir must contain, in addition to a subdirectory called model as above, two directories, seed and corpus.

<RootDir>---<NewModel>--- seed
			  corpus --- corpus_train_<NewModel>.mecab 
			  model 

'seed' dir must contain your new dictionaries. 'corpus' dir must contain your training corpus, named corpus_train_<NewModel>.mecab

'model' dir is where the new model is outputted, so you don't have to put anything beforehand. Moreover, the process also spawns result files in the corpus dir.

The evaluation results are outputted to the standard output.


