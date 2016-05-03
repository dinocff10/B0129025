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
//////////////////////////////1.
import thinkdsp
sin=thinkdsp.SinSignal(100,amp=1)
squ=thinkdsp.SquareSignal(100,amp=1)
tri=thinkdsp.TriangleSignal(100,amp=1)
saw=thinkdsp.SawtoothSignal(100,amp=1)
sin.plot()
squ.plot()
tri.plot()
saw.plot()
sinwave=sin.make_wave()
squwave=squ.make_wave()
triwave=tri.make_wave()
sawwave=saw.make_wave()
sinspec=sinwave.make_spectrum()
squspec=squwave.make_spectrum()
trispec=triwave.make_spectrum()
sawspec=sawwave.make_spectrum()
sinspec.plot()
squspec.plot()
trispec.plot()
sawspec.plot()

////////////////////////////////////////////////////2.
signal=thinkdsp.ExpoChirp(start=100,end=1000)
wave=signal.make_wave(duration=10)
spectrum=wave.make_spectrum()
spectrum.plot()
spectrogram=wave.make_spectrogram(seg_length=1024)
spectrogram.plot()

/////////////////////////////////////////////////////3.
import pylab as pl
import pandas as pd
import numpy as np
csv=        pd.read_csv('_taiwanStock.csv')
priceData=  csv.Point.values
f= open('_taiwanStock.csv')
s= f.read()
sL= s.split('\n')
xL= [x.split(',')[-1] for x in sL]
yL= [float(x) for x in xL[1:-4]] # 1:-4 
pData= np.array(yL)
print(len(pData))
def movingAverage(x, length):
    y= np.convolve(x, np.ones(length)/length)
    y= y[:len(x)]
    return y

ma100=  movingAverage(pData, 100)
ma500=  movingAverage(pData, 500)
ma1000= movingAverage(pData, 1000)

pl.plot(pData)
pl.plot(ma100)
pl.plot(ma500)
pl.plot(ma1000)

wsignal=thinkdsp.UncorrelatedGaussianNoise()
wNoise=wsignal.make_wave(duration=0.5,framerate=27018)
psignal=thinkdsp.PinkNoise()
pNoise=psignal.make_wave(duration=0.5,framerate=27018)
rsignal=thinkdsp.BrownianNoise()
rNoise=rsignal.make_wave(duration=0.5,framerate=27018)
wNoise.plot()
pNoise.plot()
rNoise.plot()
wSpec = wNoise.make_spectrum()
pSpec = pNoise.make_spectrum()
rSpec = rNoise.make_spectrum()
wSpec.plot()
pSpec.plot()
rSpec.plot()
df = pd.read_csv('_taiwanStock.csv', nrows=1625, parse_dates=[0])
ys = df.Point.values
ts = np.arange(len(ys))
wave = thinkdsp.Wave(ys, ts, framerate=1)
wave.plot()
thinkdsp.thinkplot.config(xlabel='Time (days)')
spectrum = wave.make_spectrum()
spectrum.plot_power()
thinkdsp.thinkplot.config(xlabel='Frequency (1/days)',
                 xscale='log', yscale='log')
spectrum.estimate_slope()[0]
