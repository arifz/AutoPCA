# AutoPCA: Principal Components Analysis (PCA) for a moving window in a time series. 

Normally, PCA is used to reduce the number of features, when the number of features is very large. The situation here is that we have a long time series that has been measured at a per second rate. The data is highly redundant, because the actual process is significantly slower than the sampling rate. My problem is to find the "appropriate sampling rate." There are a number of ways to approach this problem. From a signals perspective, we could try to take a Fourier Transform of the time series, and find out at what frequencies most of the energy was located, and then sample as double that frequency or a bit more. A time-series approach would be to look at the auto-correlation. I thought that PCA might be another intersting alternative.

I considered selecting a "large" window size, say 60 points, to make a one minute interval. Then as the window moves across the time series, we can use PCA to see how many independent components are needed to recreate the 60 points. If the series is very slowly moving, then one or two components should suffice to describe the entire set of sixty points. In this case, we might consider a larger window size. If on the other hand the process is changing rapidly, PCA would indicate that there is not much compression possible.

The concept is similar to auto-correlation (hence the name auto-PCA), where instead of looking for correlation between features, we look at the correlation across a moving window in a single time series. This is an actual problem, involving a very large dataset, that took me a few days to solve. 

In a jupyter notebook, I go through my own thinking and learning as I went. Along the way there are a number of very interesting and useful nuggets that are worth knowing, and are not commonly known. Bear with me and I expect that it will be educational even if you are an old-timer.

Some parts of this are about python and pandas, while others are about numpy and mathematics. Most of it would be useful for intermediate/advanced data analysts.

If you are interested in just the final result, look at the end of the notebook, and you will find the AutoPCA class and an example of its use. It is extremely fast and can tackle very large problems.
