# TREMOR12P

This module is a companion to the [TREMOR12](https://github.com/DigNeurosurgeon/TREMOR12) iPhone application that records 12 tremor parameters and exports them as a CSV file. This module contains of a iPython notebook file that performs automated data processing of the CSV file, including an example data set.

> The Watch version is in development and so is the processing code. Currently (Jan 10, 2016) only the accelerometer is available, unfortunately without timestamp.

## Requirements

- Python 3 (tested with 3.12; the notebook was written for Python 3.4 and the Anaconda distribution)
- [Jupyter Notebook](https://jupyter.org) (or JupyterLab)
- [NumPy](http://www.numpy.org), [pandas](http://pandas.pydata.org) and [matplotlib](http://matplotlib.org)

Easiest: install [Anaconda](https://www.anaconda.com/download), which includes all of them, or `pip install jupyter numpy pandas matplotlib`.

## How to use

1. Record with TREMOR12 on the iPhone and export the CSV file (share button).
2. Copy the file next to the notebook and set `pref_filename` in the first code cell.
3. Run `jupyter notebook TREMOR12P.ipynb` and run all cells. `tremor_samples.csv` is an example data set.

## Tremor frequency analysis

The notebook contains a section with a power spectrum (`np.fft.rfft`, Hann window) of acceleration and rotation speed, the effective sampling rate (estimated from the time stamps) and the dominant frequency in a tremor band that you can set (default 3-12 Hz). These are descriptive research values, not a diagnosis. Thanks to the issue reporter for the suggestion.

## Note on files from TREMOR12 version 1.1 and older

Those files have the header `roll,pitch,yaw`, but the values are in the order roll, yaw, pitch: the pitch and yaw labels are swapped (check: with the phone lying flat, the roll value follows the gravity X component and the pitch value follows the gravity Y component). The notebook corrects this automatically. Files from TREMOR12 version 1.2 onwards have the correct header `roll,yaw,pitch`. If you used the pitch or yaw columns of older files in your own analysis, swap them.
