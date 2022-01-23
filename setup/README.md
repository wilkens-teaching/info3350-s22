# Set up a virtual environment for the course

**Everything below happens in a terminal window/command prompt.**

  * Open a terminal window and run `conda`. If it works, move to the next step. If not, download and install [`miniconda`](https://docs.conda.io/en/latest/miniconda.html) or [`miniforge`](https://github.com/conda-forge/miniforge) (the latter especially for Apple M1 systems).
  * Grab course package list file from GitHub (`info-3350-packages.txt` in this directory), then:


```
conda update conda
conda config --append channels conda-forge
conda create --name 3350 --file info-3350-packages.txt
```

  * Install some data files. You can skip the last line (installing spaCy's `en_core_web_lg` model) for now if you're tight on disk space.

```
conda activate 3350
python -m nltk.downloader punkt wordnet vader_lexicon snowball_data sentiwordnet treebank
python -m spacy download en_core_web_sm
python -m spacy download en_core_web_lg
```

  * From now on, **always and only** run `conda` (to install/update packages) and JupyterLab (to use your python environment) from the command line. Always first activate the `3350` virtual environment.

```
conda activate 3350
jupyter lab
```