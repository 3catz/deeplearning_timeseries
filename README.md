# Using Wavelets and stacked LSTMs to model time series
The power consumption time series can be found in the UCI machine learning repo.
Data Preprocessing method was denoising/wavelet reconstruction, using the Haar 
wavelet, level = 2. Soft thresholding done on the approximation coefficients,
then signal reconstructed. Global reactive consumption used as target, the other
fields as features. Used both single and stacked LSTMs. The stacked LSTM
had 2 dense layers after it. The wavelet-reconstructed time series had better results 
when used through the stacked LSTM/dense layer architecture. 




