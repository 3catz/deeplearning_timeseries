# Using Empirical Mode Decomposition and Convolutional Neural Networks for Time Series Forecasting.

Data driven time-frequency analysis allows us to analyze amplitude and frequency changes of signals and time series. Empirical Mode Decomposition (Huang 1998) is a form of additive decomposition that does not rely, at least in its execution, any predefined basis functions, as you might find in Fourier Analysis or wavelet based methods. 


In this sense, it is superior to both Fourier spectral analysis and wavelet type methods in terms of the power of its analysis.
The algorithm centers around a sifting process which produces Intrinsic Mode Functions, which are orthogonal oscillating components of the signal. The process works more or less as a dyadic filter bank, meaning that with each successive IMF, the frequency of the oscillation is roughly halved. What is left after the sifting process-the specifics depending on the algorithm and methods one is using--is the residue, which is like the trend that one gets from detrending in an ARIMA context.

Ensemble Empirical Mode Decomposition, used in many of the experiments here, is an improvement on the traditional EMD algorithm, and produces more accurate IMFs With accurate IMFs, there is temporal information in the frequency data, allowing us to see, in the case of physical or real time series, how various actual cycles--diurnal, seasonal, annual, etc. meaningfully impact the values of the time series.

In the notebooks collected here, I use a variety of real and synthetic time series of varying lengths, usually from 5k-10k data points, to experiment with how EMD can help us with forecasting. The idea is that we have a univariate time series--one "sensor", gathering information--and we use EMD to analyze to decompose the signal. I use most of the data for training and leave at least 1000 points for out of sample forecast testing. The EMD process is, crucially, only done on the training data, for else information from the future contaminates what we are doing with the past. 

I pose the problem as this -- given a particular window -- e.g. 5, 10, or 20 points -- I want to forecast the next value in the time series. I use deep learning methods--in particular, convolutional neural networks with dilation, residual connections, sometimes recurrent networks -- to forecast the next value in the time series *in its decomposed form*. We do this because perhaps, in the future, we want to know not only the forecast, but have some "guess" or estimate of how the series would be decomposed. We cannot collect IMF information in the future, because we only have one sensor.  


