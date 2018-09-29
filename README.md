# Using Empirical Mode Decomposition and Convolutional Neural Networks for Time Series Forecasting.

EMD is a method of breaking down a signal without leaving the time domain. It can be compared to other analysis methods like Fourier Transforms and wavelet decomposition. The process is useful for analyzing natural signals, which are most often non-linear and non-stationary. The algorithm centers around a sifting process which produces Intrinsic Mode Functions--orthogonal oscillating components of the signal. The process works more or less as a dyadic filter bank, meaning that with each successive IMF, the frequency of the oscillation is roughly halved. What is left after the sifting process-the specifics depending on the algorithm and methods one is using--is the residue, which is like the "trend" that is leftover when you use ARIMA type methods. 

Ensemble Empirical Mode Decomposition, used in many of the experiments here, is an improvement on the traditional EMD algorithm. It introduces some noise into the process, so that the IMFs produced on the other end should be more accurate.

In the notebooks collected here, I use a variety of real and synthetic time series of varying lengths, usually from 5k-10k data points, to experiment with how EMD can help us with forecasting. I only performed EMD on the training set, and used the EMD time series NOT as input features--but as targets--so that the network could learn how to go from a sequence of 20 lagged values of the time series to a sequence of the IMF components that, added together, comprise the next value of the series. 

I did this way because I didn't want to assume that you could always do EEMD and retrain the network every time you observed new data--the idea was to used something "pretrained" so that you could take the last 20 values and forecast the next IMF values, which, after the fact, would be added together to produce a forecast for the original series itself. This way not only do you get the forecast but you retain some sense of how the dynamic of the various components going forward.

There's not a lot of literature out there covering the hybrid approach of using EEMD and convolutional neural networks--there are papers using EMD + other machine learning methods, like SVM, and there are papers about fully convolutional networks using ablation, else known as dilated kernels, but not many trying to combine the two. I wanted to see what could be done when we bring some of the best techniques from time series analysis in applied mathematics, natural science and engineering and combined with the latest techniques in deep learning. There were times when it worked fairly well, and beat out a XGBoost Regression model that I ran using AutoML, and other times when they seemed to be neck and neck. 





