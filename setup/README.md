# Set up a virtual environment for the course

Below are instructions to install, update, and use the correct python programming environment for the course. We'll walk through this during the first section meeting, but here's the compressed version for those who want to get a head start.

**Everything below happens in a terminal window/command prompt.**

  * Open a terminal window and run `conda`. If it works, move to the next step. If not, download and install [`miniconda`](https://docs.conda.io/en/latest/miniconda.html) or [`miniforge`](https://github.com/conda-forge/miniforge) (the latter especially for Apple M1 systems).
  * Download the course package list file from GitHub (`info-3350-packages.txt` in this directory). Pay attention to where you've saved it. Then:


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

  * From now on, **always and only** run `conda` (to install/update packages) and JupyterLab (to use your python environment) from the command line. Always first activate the `3350` virtual environment, like so:

```
conda activate 3350
jupyter lab
```

* If you need to update your install during the semester (unlikely, but not impossible), first re-pull the package list from GitHub, then:

```
conda update conda
conda activate 3350
conda update --file info-3350-packages.txt
```