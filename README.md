## stamatatos07 - An Approach to Authorship Attribution

This is a reimplmentation of the approach to authorship attribution originally described in

> E. Stamatatos. [Author identification using imbalanced and limited training texts](http://www.icsd.aegean.gr/lecturers/stamatatos/papers/tir2007.pdf). In Proc. of TIR, pp. 237- 241, 2007 [[paper](http://www.icsd.aegean.gr/lecturers/stamatatos/papers/tir2007.pdf)]

It was reimplemented as part of a science reproducibility study alongside [14 other authorship attribution approaches](https://github.com/search?q="Who+wrote+the+web"+user:pan-webis-de). The results of the reproducibility study can be found in

> Martin Potthast, Sarah Braun, Tolga Buz, Fabian Duffhauss, Florian Friedrich, Jörg Marvin Gülzow, Jakob Köhler, Winfried Lötzsch, Fabian Müller, Maike Elisa Müller, Robert Paßmann, Bernhard Reinke, Lucas Rettenmeier, Thomas Rometsch, Timo Sommer, Michael Träger, Sebastian Wilhelm, Benno Stein, Efstathios Stamatatos, and Matthias Hagen. [Who Wrote the Web? Revisiting Influential Author Identification Research Applicable to Information Retrieval](http://www.uni-weimar.de/medien/webis/publications/papers/stein_2016d.pdf). In Advances in Information Retrieval. 38th European Conference on IR Resarch (ECIR 16) volume 9626 of Lecture Notes in Computer Science, Berlin Heidelberg New York, March 2016. Springer. [[paper](http://www.uni-weimar.de/medien/webis/publications/papers/stein_2016d.pdf)] [[bib](http://www.uni-weimar.de/medien/webis/publications/bibentries.php?bibkey=stein_2016d)]

If you use this reimplementation in your own research, please make sure to cite both of the above papers.

## Usage

To execute the software, install it and make sure all its dependencies are installed as well; then run the software using the following command:

`python n_gram.py -i <path-to-input-data> -o <output-path>` (tentative)

## Input and Output Formats

The software accepts authorship attribution datasets that are formatted according to the correspondong [PAN shared task on authorship attribution](http://pan.webis.de/tasks.html). A number of [datasets can be found there](http://pan.webis.de/data.html), and all of them are formatted as follows.

In a dataset's `TOP_DIRECTORY`, a `meta-file.json` is found which comprises

  - the language of the texts within (e.g., EN, GR, etc.),
  - the names of the subdirectories that contain texts from candidate authors,
  - the name of the subdirectory that contains texts of unknown authorship, and
  - the name of each file of unknown authorship that is to be attributed to one of the candidate authors.
  
The software accepts as input a path to an inflated dataset's `TOP_DIRECTORY` and starts the authorship attribution process from there. The output in the `OUTPUT_PATH` will be a file `answers.json` formatted as follows:

```json
{
"answers": [
	{"unknown_text": "unknown00001.txt", "author": "candidate00001", "score": 0.8},
	{"unknown_text": "unknown00002.txt", "author": "candidate00002", "score": 0.9}
	]
}
```

where `unknown_text` is the name of an unknown text as per `meta-file.json`, `author` is the name of a candidate author as per `meta-file.json`, and `score` is as real value in the range [0,1] which indicates the software's confidence in its attribution (0 means completely uncertain, 1 means completely sure).

## License

Copyright (c) 2015 Bernhard Reinke

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.



# Old; remove later
Stamatatos, E. (2007). Author identification using imbalanced and limited training texts. In Proceedings of the 4th International Workshop on Text-based Information Retrieval (pp. 237- 241).

Dissimilarity function, where only n-grams from the test text profile are considered. 

# How to use this implementation
This code is written in Python 2.7

To run the main program of n_gram.py, both files (jsonhandler.py and n_gram.py) must be stored in the same folder together with a subfolder which is called in the last line of n_gram.py.

The subfolder must include:
- candidates' trainings set
- set of unknown texts
- meta-file

The results are saved to the json-file out.json in in the subfolder.
