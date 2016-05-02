# B0129025 test
//https://github.com/AllenDowney/ThinkDSP/blob/master/code/chap04soln.ipynb//

import numpy as np
import pandas as pd
signal=thinkdsp.UncorrelatedGaussianNoise()

wave=signal.make_wave(duration=0.5,framerate=4230)

spectrum = wave.make_spectrum()
spectrum.plot()

spectrum.plot_power()
thinkdsp.thinkplot.config(xlabel='Frequency (1/days)',
                 xscale='log', yscale='log')
                 
  spectrum.estimate_slope()[0]               
