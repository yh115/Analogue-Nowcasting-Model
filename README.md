# Analogue-Nowcasting-Model
## Table of Contents
- [Proposal](#Proposal)
- [Reference Papers](#Papers)
- [Data](#Data)
- [CNN Autoencoder](#Autoencoder)

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

### Understanding the Autoencoder:

An autoencoder is a type of neural network used for unsupervised learning. It aims to encode the input data into a lower-dimensional latent space (encoding) and then decode it back to its original form (decoding). The encoder and decoder are trained together to minimize the difference between the input and the output (reconstruction loss).

### Application to Weather Parameters:

Given the provided scenario, the weather parameters (Geopotential height z, Winds vectors u and v, etc) across different pressure levels and times can be treated as multi-dimensional data. This data can be input into the CNN autoencoder.

**Encoding:** The encoder part of the CNN autoencoder captures the most crucial features or patterns present in the weather parameters. It reduces the data's dimensionality while retaining its significant characteristics.

**Decoding:** The decoder then tries to reconstruct the original weather parameters from the encoded form.

### Finding Similarities:

Once the autoencoder is trained, the encoder part can be used to transform any given weather data into its lower-dimensional encoded form.

For a given day's weather data (like today), you can pass it through the encoder to get its encoded representation.

The same can be done for all the days in the historical database. Thus, every day's weather parameters are represented as points in this lower-dimensional latent space.

To find the most similar day to today, you can compare the encoded representation of today's weather with the encoded representations of all days in the historical database. The day with the nearest encoded representation (using a metric like Euclidean distance) is considered the most similar.

### Why CNN for Weather Data?

CNNs are particularly suited for grid-like structured data, such as images. In the context of weather data, the parameters across latitude and longitude can be seen as an image where each pixel or grid cell represents a weather parameter's value. The convolutional layers can capture spatial hierarchies and patterns in this data, making CNNs a good fit for this type of analysis.

**Feature Learning:** The CNN autoencoder learns to capture the most crucial features in the weather data automatically. This means it can identify patterns or features in the data that are significant for similarity without being explicitly told what to look for.

**Noise Reduction:** Autoencoders can help denoise data. If there are small inconsistencies or noise in the weather readings, the autoencoder can help smooth these out, focusing on the larger patterns.

**Historical Comparison:** By comparing the encoded representations, we're essentially comparing how similar the patterns and features in the weather data are, not just the raw values. This can provide a more holistic comparison, considering all the weather parameters together.


### ResNet (Residual Networks):

ResNet is a type of CNN introduced to combat the vanishing gradient problem in deep neural networks. As neural networks grow deeper, the gradients during training can become so small that the network becomes hard to train. ResNet introduces "skip connections" or "shortcuts" that allow gradients to flow through the entire network more easily.

The key innovation in ResNet is the introduction of a "residual block." Instead of trying to learn an underlying function directly, ResNets try to learn the residual function (or the difference) from the identity mapping. This residual learning mechanism allows ResNets to be trained for a large number of layers without significant loss in performance.

https://cv-tricks.com/keras/understand-implement-resnets/#:~:text=The%20major%20differences%20between%20ResNet,the%20form%20of%20identity%20connection.


