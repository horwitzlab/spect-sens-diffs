## *Spectral sensitivity differences between rhesus monkeys and humans*
This repository contains data used in the manuscript by Lindbloom-Brown, Tait,
and Horwitz entitled "Spectral sensitivity differences between rhesus monkeys
and humans: Implications for neurophysiology", which is under review as of June
2014.

Here we provide three MATLAB .mat files that contain the data from three
experiments presented in the manuscript.

#### Experiments 1 and 2 - detection of 15 Hz modulations of the green and blue phosphors or of all phosphors
* `monitor_spectra` - Each column is the spectral power distribution of the red,
  green, and blue color channels (respectively, each 81 elements long) of the
  displays used in our experiments. Because we calibrated our displays
  periodically, each trial in `trials.data` (below) contains a column index into
  this matrix to indicate the calibration used at the time of data collection.
* `cone_sensitivities` - The Stockman, MacLeod, and Johnson 10-degree human cone
  fundamentals that we use to compute cone contrasts.
* `background_cc` - The background of our display in human cone contrast units.
  Just like `monitor_spectra` above, each column is indexed (in `trials.data`) to
  reflect the background color at the time of data collection.
* `wavelengths` - The wavelength sampling lattice of `monitor_spectra` and `cone_sensitivities`.
* `trials` - a struct array with two fields: 1) `subject` is the identity of the
  psychophysical observer, and 2) `data` houses the trial-by-trial data of each
  subject as a matrix. The columns of `data` are:
  1. the L-cone contrast;
  2. the M-cone contrast;
  3. the S-cone contrast;
  4. the retinal eccentricity of the stimulus in degrees (negative values
     indicate presentation to the left of the fixation spot);
  4. `true` if the observer detected the stimulus and `false` otherwise;
  5. a column index into `monitor_spectra`;
  6. a column index into `background_cc`.

#### Experiment 3 - low frequency scotopic detection
* `monitor_spectra` - This has the same layout as above and was measured
  **without** the application of neutral density filters;
* `scotopic_lum_eff` - The CIE scotopic luminous efficiency function;
* `nd_transmittance` - The measured transmittance of a 1.0-log unit Kodak Wratten
  96 neutral density filter;
* `wavelengths` - The wavelength sampling lattice of `monitor_spectra`,
  `scotopic_lum_eff`, and `nd_transmittance`;
* `trials` - Like the first two experiments, this struct array contains
  trial-by-trial data from each subject. The columns of `data` are:
  1. the scotopic luminance of the stimulus;
  2. the retinal eccentricity of the stimulus in degrees (negative values
     indicate presentation to the left of the fixation spot);
  3. `true` if the observer detected the stimulus and `false` otherwise;
  4. `1` for a green channel modulation or `2` for the blue channel;
  5. a column index into `monitor_spectra`;
