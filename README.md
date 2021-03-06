# PCFG Parser Evaluation

## 1. Objective

We compare the performance of two famous parsers; the **Berkeley parser** and the **Stanford parser**. In order to measure their performances, we test them on 3 test files containing test sentences and evaluate their performance with respect to the corresponding gold standard parse trees in test gold files.

## 2. Parsers

We have compared these two famous parsers. They are available in the websites mentioned below.

* [**Berkeley Parser**](https://github.com/slavpetrov/berkeleyparser)
* [**Stanford Parser**](http://nlp.stanford.edu/software/lex-parser.shtml)

## 3. Test files

We have 3 sets of test files. Each set contained a `{1, 2, 3}.plain` file which have the test sentences. They also contain a `{1, 2, 3}.gold` file which has the corresponding parse trees for the test sentences in the `.plain` files. Along with these, we have also appended these files together to create the `Overall` test file and the corresponding Overall gold standard parse file.

## 4. Files in this project

Here is the list of filesin this project and their purposes for ready reference. The files are:
* **README**: This file contains the complete comprehensive details of the entire assignment.
* **new.prm**: This is the parameter file that was used for the EVALB evaluation. A few parameters were changed which have been discussed in the Evaluation section (6) below.
* **lexparser_modified.sh**: This is the modified shell script file which was used for the Stanford parser. Details about the changes are mentioned in the Preprocessing for Stanford Parser section (7) below.
* **“Berkley” folder**: This folder contains the following files:
  1. Parsed files of Berkeley parser
  2. Labeled results of EVALB evaluation
  3. Unlabeled results of EVALB evaluation
* **“Stanford” folder**: Similar to the Berkeley folder, just for the Stanford parser.
* **“Significance_tests” folder**: This folder contains the results of Approximate Randomization method for unlabeled and labeled data for the threshold probabilities of `0.5`, `0.05` and `0.01`.
* **remove_ROOT.py**: Python script for postprocessing the parse trees generated by the Stanford parser to remove the `ROOT` node from the trees.
* **sig_test.py**: Python script containing the entire implementation of the Approxiimate Randomization evaluation method.

## 5. Procedure

We have measured the performance of the parsers using the following metrics:
* **Labeled precision**
* **Unlabeled precision**
* **f-score**
* **Recall**

Apart from this, we have also considered evaluating a significance test for both the parsers. For this, we have tried to use the **Approximate Randomization** significance test for both of these parsers where we have only compared the f-score values of both for evaluation.

## 6. Evaluation

We have used the free-to-use standard scoring tool for constituency parsing [**EVALB**](http://nlp.cs.nyu.edu/evalb/) for recording the different evaluation metrics in this process. However, we had to perform some preprocessing steps which we have mentioned in the next section below.

## 7. Preprocessing for Stanford Parser

We had to perform this preprocessing step for the Stanford parser to get the output in proper format. We are using the pre-defined shell script lexparser.sh. However, we had to add few parameters in the shell script so that we get the desired output.

The parameters that we added were as follows:
`java -mx1000m -cp "$scriptdir/*:" edu.stanford.nlp.parser.lexparser.LexicalizedParser \ -sentences newline -tokenized -outputFormat oneline edu/stanford/nlp/models/lexparser/englishPCFG.ser.gz $*`

We have provided the modified version for of this shell script in the zip file archive. The file is named **lexparser_modified.sh**.
