# QB Hackathon DARE

In order to have the required installation, please run in terminal the following command:

> ```pip: -r requirements.txt```

If you want to use the notebooks, it assums that the data is uploaded in the repository:

>       README.md
>       notebooks
>       ..
>       data ->
>       +-images ->
>       |    +-plume ->
>       |    |     images ....
>       |    |     |
>       |    |     |_
>       |    +-no_plume ->
>       |    |     images ....
>       |    |     |
>       |    |     |_
>       |    +-metadata.csv
>       +-test data ->
>       |    +-images ->
>       |    |   images ...
>       |    |    |
>       |    |    |
>       |    +-metadata.csv

This repository has a data augmentation notebook, which quadruples the size of our dataset. The [notebook](data_augmentation.ipynb) explains what was done in more details.

We have trainied two models:
-> One for image classification of whether or not there is a leak
-> A model that, assuming the presence of a leak, predicts its position on the image.

The training of those 2 models was done in the [data_augmentation](model_training.ipynb) notebook.

We have prefered to go for a model from scratch rather than using transfer learning and pre trained model which were working as well as our model while being much more complicated to implement, and heavier to use. In fact, the higher number of weights makes it less usuable in drones which have small computational power, one of our potential use case.

For clarity, we have ommited the hyper parameter search as many of the models we have tried had essentially the same structure but with different drop out rates, more or less keras.Conv2D layers, normalization, etc..
For the learning rate, we have generated linearly learning rates and then applied an inverse exponential with proper scaling to obtain a non linear search of hyparameters.
