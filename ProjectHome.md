Please feel free to email the authors if you need help on using PyEEG in your research.

**Note: I wrote PyEEG a long time ago as a fresh Pythonist - I didn't even know there were things like map() or list comprehension at that time. So it looks ugly.
Heavy rewriting is under way. You will see shorter and more elegant code soon.**

# About the game #
  * PyEEG is a Python module (i.e., function library) to extract EEG (Electroencephalography) [features](#Features.md). [More functions](#Coming.md) are being added.
  * It contains functions to build data for feature extraction, such as building an embedding sequence from a given time series. It is also able to export features into svmlight format for calling machine learning tools.  [Check non-feature extraction functions below](#Non-features.md).
  * In PyEEG, EEG series are represented in Python list or numpy array data structure. Therefore, PyEEG can not read or load files, such as EDF+ or even ASCII file. You can use other open source tools, (e.g.,[EDFBrowser](http://www.teuniz.net/edfbrowser), [BioSig](http://biosig.sourceforge.net/), [EEGLab](http://sccn.ucsd.edu/eeglab/)), to load and convert files before feeding EEG data into PyEEG.
  * This library is initially used in epileptic EEG recognition against normal EEG. But it can be extended to other neurological disease analysis based on same features.
  * **Disclaimer**: PyEEG may NOT be used in safety-critical applications, such as life-support medical systems. The author is NOT responsible for any consequences. For research and educational purpose only.

# Download, Use and Help #
  1. Download pyeeg.py. Check "Download" tab with the highest version number.
  1. Save it as "pyeeg.py" under current Python search path.
    * The easiest way is to put it under your work directory, where you run your code (the code that calls functions in pyeeg)
    * You can set the system environment variable PYTHONPATH to the directory you save pyeeg.py
  1. Import pyeeg in your Python code as you import other modules. The module name is pyeeg.
  1. _Please_ cite PyEEG if you use it in your research and publication:
> > Forrest S. Bao, Xin Liu and Christina Zhang, "PyEEG: An Open Source Python Module for EEG/MEG Feature Extraction," Computational Intelligence and Neuroscience, March, 2011
  1. **If your project is using PyEEG,** please do let me know! I will be happy to help you use PyEEG better for your project.
  1. Mailing list: http://lists.sourceforge.net/mailman/listinfo/pyeeg-user (Subscription needed to post).
  1. If you are sure about a bug, please report in Issues tab.

# Documentations #
  * Docstrings in the source code. Each function has very detailed comments following Numpy documentation guideline in reST language.
  * Reference guide generated from docstrings. For PDF version, check "Download" tab. For HTML version, check here: http://pyeeg.sf.net
  * A short tutorial is given in Section 4 of [our paper](http://www.hindawi.com/journals/cin/2011/406391/)

# Contributing to PyEEG #
  1. Functions: Your code is more than welcome to be added into PyEEG. Please email me and I will add you as a committer.
  1. Documentation: Don't hesitate to email me if you wanna help me polish the wiki or reference guide.
  1. Feature requesting: Please feel free to buzz me for new features you wanna see in PyEEG.

# Projects using PyEEG #

> Let me know your exciting project using PyEEG!
  * [Andreas Klostermann](http://www.andreasklostermann.de) wrote a Linux driver for [NeuroSky MindWave EEG set](http://www.neurosky.com/People/WhatWeDo.aspx) and included PyEEG into a set of Python scripts that interface with Neurosky Mindwave. His project is at https://github.com/akloster/python-mindwave A video about it is here: http://www.youtube.com/watch?v=1ylndEyVuso

# Functions #
For function details, please refer to the documentations.

## Features ##
Currently, these functions have been implemented (EEG signals are time series of Python list or numpy array type):
  * bin\_power(), Power Spectral Density (PSD), spectrum power in a set of frequency bins, and, Relative Intensity Ratio (RIR), PSD normalized by total power in all frequency bins
  * pfd(), Petrosian Fractal Dimension (PFD)
  * hfd(), Higuchi Fractal Dimension (HFD)
  * hjorth(), Hjorth mobility and complexity
  * spectral\_entropy(), spectral entropy, the entropy of RIRs
  * svd\_entropy(), Singular Value Decomposition (SVD) entropy
  * fisher\_info(), Fisher Information, the entropy of SVD values, i.e., SVD spectrum
  * ap\_entropy(), Approximate Entropy (ApEn)
  * samp\_entropy(), Sample Entropy (SampEn)
  * dfa(), Detrended Fluctuation Analysis (DFA)
  * hurst(), Hurst Exponent (Hurst)

## Non-features ##
These functions are built to compute some features or for your convenience to build more functions
  * pyeeg.first\_order\_diff(), first order differential sequence of input series

## Coming ##
  * Singular Value Fraction (SVF)
  * Permutation Entropy
  * Information Based Similarity (IBS)

# pyeeg does not extract these features #

I do not want to reinvent the wheel. There are many features used in EEG pattern recognition and signal processing which are basic scientific parameters. So please take advantage of scipy standard libraries. I list some functions you can use:
  * I think I needn't to mention mean, standard deviation, FFT.
  * skewness, scipy.stats.skew(a, axis=0, bias=True), http://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.skew.html
  * kurotsis, scipy.stats.kurotsis(a, axis=0, fisher=True, bias=True), http://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.kurtosis.html