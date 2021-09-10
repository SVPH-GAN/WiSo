<div align="center">
# SuperEnergyBench: Evaluating Super-Resolution Models on US Wind and Solar Data

Caltech SURF Project for 2020-2021

Rupa Kurinchi-Vendhan, Lucien Werner, Björn Lütjens, Ritwik Gupta

## Abstract
As the United States constructs additional renewable wind and solar energy power plants, policy makers in charge of operational decision making, scheduling, and resource allocation are faced with challenges introduced by the variability in spatial resolution in solar irradiance and wind speeds. Physics-based short-term forecasting models predict wind speeds and solar irradiance fields at coarse resolutions. Thus, machine learning-based super-resolution methods have been developed to provide higher fidelity for decision making. We generate a machine-learning ready dataset of wind and solar data from NREL databases. Additionally, we present a benchmark of super-resolution methods against this data. In addition to simple interpolation methods, we investigate three machine learning methods: the physics-informed resolution-enhancing generative adversarial network (PhIREGAN) model, an enhanced deep super-resolution (EDSR) network, and the enhanced super-resolution generative adversarial network (ESRGAN). \footnote{The processed benchmark dataset and code will be published at \href{https://github.com/RupaKurinchiVendhan/SuperEnergyBench}{this GitHub repository.}}

<div align="left">

## Dataset
The dataset used for this project is available through the "data.ipynb" notebook. This file also contains instructions for generating your own machine learning-ready dataset, with flexibility to change the parameters inputted to NREL's WIND Toolkit and NSRDB.

## Training
To train the PhIREGAN, ESRGAN, or EDSR models to achieve 5x super-resolution (SR), use the following commands.

**PhIREGAN**

`main.py --model=phiregan --mode=train --data_dir=path/to/train/data --data_type=data_type`

Here, `data` should be a folder of TFRecords. The `data_type` can either be `wind` or `solar`. To train the SR CNN, replace `phiregan` with `srcnn`. 

**ESRGAN**

`main.py --model=esrgan --mode=train --data_dir=path/to/train/data`

As opposed to the PhIREGAN, the data directories for EDSR and ESRGAN must be a folder with HR and LR subdirectories of images. 

**EDSR**

`main.py --model=edsr --mode=train --data_dir=path/to/train/data --valid_dir=path/to/valid/data --cuda=0`

## Testing
Once you have trained your models, use the commands below to run them on test data.

**PhIREGAN**

`main.py --model=phiregan --mode=test --data_dir=path/to/test/data --data_type=data_type`

To test the SR CNN, replace `phiregan` with `srcnn`.

**ESRGAN**

`main.py --model=esrgan --mode=test --data_dir=path/to/test/data --save_dir=path/to/save`

Here, `save_dir` is the directory where SR outputs should be saved.

**EDSR**

`main.py --model=edsr --mode=test --data_dir=path/to/test/data --save_dir=path/to/save --model_path=path/to/model --cuda=0`

