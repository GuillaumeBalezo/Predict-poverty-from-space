# Predict-poverty-from-space
Prediction of African country's wealth thanks to satellite imagery.


# Overview :

The goal of this project is to predict the wealth of African country's regions. To achieve that, we have, for any region, its coordinates, a satellite image and the associated nightlight intensity.

First, we try to predict wealth only with nightlight intensity of the region. It is a classical regression problem. We first implement simple parametric regression models such as linear and ridge regression in **regression_models.ipynb**. To go beyond these simple models, there exists nonparametric models mainly based on well-known kernel methods, of which we develop the theory in **kernel_methods.ipynb**. We observe that data behave differently according to nightlight intensity values (in particular near to zero). We then modelize data around 0 thanks to basic density estimation techniques in **density_estimation.ipynb**.

Then, we try to predict wealth with nightlight intensity and coordinates of the region. Instead of trying again previous techniques, we directly use gaussian process in **gaussian_process.ipynb**, which are supposed to be good when data are spatially correlated.

Finally, we try to predict wealth with deep features extracted from a CNN whose input is the satellite image of the region. We begin by training a CNN to predict nightlight intensity, given satellite images. Hence, it is able to extract meaningful features from satellite images. We then train it again on the wealth prediction task, by initialising it with previously learned parameters.

As an aside, we want two combine to good methods : gaussian processes and CNN. To do that, we implement a CNN from scratch in **neural_net_from_scratch/** and write the gaussian process as an allowed layer. To train it, we can use conventional methods based on gradient descent but we also try to train this CNN with evolutionary strategies, such as CMA-ES. These optimization algorithm are explicited in **optimization_algorithms.ipynb**.


# To-do list :

Data :
- download 300,000 daytime images (~20,000) (x)

Density estimation :
- histogram density estimation (x)
- kernel density estimation (x)

Regression models :
- Parametric models : implement Lasso regression, bayesian regression
- Nonparametric models : implement SVR, splines regression, wavelets regression
- 2D models : implement gaussian process regression (x)

Neural net :
- implement conv layer (x)
- train VGG for nightlight intensities prediction (x)
- train VGG for wealth prediction (transfer learning) (x)
- semantic segmentation : implement FCN (-)
- implement gp layer (-)
- visualization and interpretation (-)

Semi-supervised learning :
- classical techniques : VAT, Mean Teacher, etc.
- SSDKL

Optimization algorithm :
- Evolutionary strategies : implement CMA-ES (x)
- implement evolution strategies for neural net parameters learning (-)
