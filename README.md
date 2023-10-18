# Analogue-Nowcasting-Model
## Table of Contents
- [Proposal](#Proposal)
- [Reference Papers](#Papers)
- [Data](#Data)
- [CNN Autoencoder](#Autoencoder)
- [Credits](#credits)
- [License](#license)

## Proposal
- [Proposal for the development of a data driven model for rainfall forecasting.docx](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981503/Proposal.for.the.development.of.a.data.driven.model.for.rainfall.forecasting.docx)

## Papers 
- [An Analog Forecast System for Precipitation Forecasting.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981265/An.Analog.Forecast.System.for.Precipitation.Forecasting.pdf)

- [Enhanced Analogue Forecast System for Precipitation by Autoencoder Feature Extraction.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981267/Enhanced.Analogue.Forecast.System.for.Precipitation.by.Autoencoder.Feature.Extraction.pdf)

- [An analogy based method for strong convection forecasts in China using GFS forecast data.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981270/An.analogy.based.method.for.strong.convection.forecasts.in.China.using.GFS.forecast.data.pdf)


## Data
**Data Details**

**Source**: ECMWF ERA5 dataset

**Time Interval**: Hourly

**Resolution:** 0.25° x 0.25°

**Parameters:**

•	Geopotential height: 925hPa, 850hPa, 700hPa.

•	Wind vectors: 925hPa, 850hPa, 700hPa.

•	Vapour Flux: 925hPa.

•	Relative humidity: 850hPa and 700hPa

**Region:** 95E - 120E longitude and 5S - 15N latitude.

**link** https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-pressure-levels?tab=form

## CNN Autoencoder

### Convolutional Neural Networks (CNN):

CNNs are a category of neural networks that have proven effective in areas such as image recognition and classification. They process data with a grid-like topology, making them particularly suited for analyzing visual data. The core operation in a CNN is the convolution operation, which helps in automatically and adaptively learning spatial hierarchies of features.

### ResNet (Residual Networks):

ResNet is a type of CNN introduced to combat the vanishing gradient problem in deep neural networks. As neural networks grow deeper, the gradients during training can become so small that the network becomes hard to train. ResNet introduces "skip connections" or "shortcuts" that allow gradients to flow through the entire network more easily.

The key innovation in ResNet is the introduction of a "residual block." Instead of trying to learn an underlying function directly, ResNets try to learn the residual function (or the difference) from the identity mapping. This residual learning mechanism allows ResNets to be trained for a large number of layers without significant loss in performance.

https://cv-tricks.com/keras/understand-implement-resnets/#:~:text=The%20major%20differences%20between%20ResNet,the%20form%20of%20identity%20connection.


