# Analogue-Nowcasting-Model
## Table of Contents
- [Proposal](#Proposal)
- [Reference Papers](#Papers)
- [Data](#Data)
- [CNN Autoencoder](#Autoencoder)

## Proposal
- [Proposal for the development of a data driven model for rainfall forecasting.docx](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981503/Proposal.for.the.development.of.a.data.driven.model.for.rainfall.forecasting.docx)

### Proposal for the development of a data-driven model for rainfall forecasting

### 1. Introduction
Singapore's tropical and maritime setting poses a unique set of meteorological challenges with the rapid changing conditions. Characterized by its high humidity, frequent rainfall, and localized convective activities, the region often faces weather phenomena that challenge traditional forecasting methods. 

Through extensive case studies, it has been observed that Numerical Weather Prediction (NWP) models have limitations in tropical convective weather predictions. The main challenges that affect NWP are complexity of convective process (cloud microphysics schemes do not cover all the parameters that can be calculated), parameterization (models are mainly generic to use and not tailor-made for the regional location as model scales aren’t specific enough). A significant advantage of analogue forecasting is that it is capable of providing realistic weather forecasts without introducing any simplifications in the physics of the atmosphere.

This paper proposes an analogue-based model that aims to enhance the short-term rainfall forecasting. The main hypothesis of analogue approach is that similar atmospheric conditions will evolve in similar ways. Thus, once an analogue is found for the current situation, the forecast for a given period of time can be obtained by the evolution of the meteorological conditions observed after that similar past situation. This is where the analogue model approach emerges as a promising alternative, especially for short-term forecasting. The analogue rainfall model can be used as an additional reference for NWP, providing a complementary perspective and potentially refining the final forecast.

### 2. Objective
•	Design an Analogue Rainfall Forecasting (ARF) model using historical data patterns.

•	Validate the model's performances.

### 3. Data Selection Rationale

**Years 2010-2022:** The selected data encompasses various climatic oscillations, inclusive of El-Niño, La-Niña, and neutral phases. Such a design criterion ensures that the model robustly accounts for the influences of the ENSO cycle on Singapore's precipitation dynamics.

**Recent Data priority:** To stay relevant amidst the rapidly evolving weather patterns caused by climate change, our focus remains on more recent data. 

### 4. Data Details

**Source:** ECMWF ERA5 dataset.

vikki115@outlook.com

Meo630528!

**Time Interval:** Hourly.

**Resolution:** 0.25° x 0.25°.

**Parameters:**
•	Geopotential height (z): 925hPa, 850hPa, 700hPa.

•	Wind vectors (u,v): 925hPa, 850hPa, 700hPa.

•	Vapour Flux (q) : 925hPa.

•	Relative humidity (rh): 850hPa and 700hPa

**Region:** 95E - 120E longitude         5S - 15N latitude.

### 4. Model design

**4.1 Method A: Event-based analogue approach**

•	Extract daily data points across the specified time frames (00UTC, 03UTC, 06UTC, 09UTC, 12UTC, 15UTC, 18UTC, 21UTC.) and parameters.

•	For each day in the validation set, calculate similarity metrics using the chosen parameters across all historical days in the training set.

•	Identify the most similar historical day and predict rainfall based on that day's actual rainfall.

**4.2 Method B: Hourly analogue approach**
•	Extract hourly data for the chosen parameters.

•	For each hour in the validation set, calculate similarity metrics using the chosen parameters against the corresponding hours in the training set.

•	Predict rainfall for the current hour based on the most similar historical hour's actual rainfall.

### 5. Validation and Testing:

70% of the data is used for training (X_train), and the remaining 30% is reserved for validation (X_val).


### 6. Expected Outcomes

•	Improved accuracy in predicting rainfall for Singapore.

•	Better understanding of individual parameter significance in different weather scenarios.



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


    ValueError: Dimensions must be equal, but are 16 and 8 for '{{node mean_squared_error/SquaredDifference}} = SquaredDifference[T=DT_FLOAT](model_1/conv3d_31/Sigmoid, IteratorGetNext:1)' with input shapes: [?,16,4,82,51,3], [?,8,4,82,102,3].

Training data shape (511, 8, 4, 82, 102, 3)
Validation data shape (220, 8, 4, 82, 102, 3)

Model: "model_15"
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to                     
==================================================================================================
input_16 (InputLayer)           [(None, 8, 4, 82, 10 0                                            
__________________________________________________________________________________________________
conv3d_242 (Conv3D)             (None, 8, 4, 82, 102 2624        input_16[0][0]                   
__________________________________________________________________________________________________
batch_normalization_150 (BatchN (None, 8, 4, 82, 102 128         conv3d_242[0][0]                 
__________________________________________________________________________________________________
activation_150 (Activation)     (None, 8, 4, 82, 102 0           batch_normalization_150[0][0]    
__________________________________________________________________________________________________
conv3d_243 (Conv3D)             (None, 8, 4, 82, 102 27680       activation_150[0][0]             
__________________________________________________________________________________________________
batch_normalization_151 (BatchN (None, 8, 4, 82, 102 128         conv3d_243[0][0]                 
__________________________________________________________________________________________________
conv3d_244 (Conv3D)             (None, 8, 4, 82, 102 128         input_16[0][0]                   
__________________________________________________________________________________________________
add_75 (Add)                    (None, 8, 4, 82, 102 0           batch_normalization_151[0][0]    
                                                                 conv3d_244[0][0]                 
__________________________________________________________________________________________________
activation_151 (Activation)     (None, 8, 4, 82, 102 0           add_75[0][0]                     
__________________________________________________________________________________________________
conv3d_245 (Conv3D)             (None, 8, 4, 82, 102 55360       activation_151[0][0]             
__________________________________________________________________________________________________
batch_normalization_152 (BatchN (None, 8, 4, 82, 102 256         conv3d_245[0][0]                 
__________________________________________________________________________________________________
activation_152 (Activation)     (None, 8, 4, 82, 102 0           batch_normalization_152[0][0]    
__________________________________________________________________________________________________
conv3d_246 (Conv3D)             (None, 8, 4, 82, 102 110656      activation_152[0][0]             
__________________________________________________________________________________________________
batch_normalization_153 (BatchN (None, 8, 4, 82, 102 256         conv3d_246[0][0]                 
__________________________________________________________________________________________________
conv3d_247 (Conv3D)             (None, 8, 4, 82, 102 2112        activation_151[0][0]             
__________________________________________________________________________________________________
add_76 (Add)                    (None, 8, 4, 82, 102 0           batch_normalization_153[0][0]    
                                                                 conv3d_247[0][0]                 
__________________________________________________________________________________________________
activation_153 (Activation)     (None, 8, 4, 82, 102 0           add_76[0][0]                     
__________________________________________________________________________________________________
conv3d_248 (Conv3D)             (None, 8, 2, 41, 51, 221312      activation_153[0][0]             
__________________________________________________________________________________________________
batch_normalization_154 (BatchN (None, 8, 2, 41, 51, 512         conv3d_248[0][0]                 
__________________________________________________________________________________________________
activation_154 (Activation)     (None, 8, 2, 41, 51, 0           batch_normalization_154[0][0]    
__________________________________________________________________________________________________
conv3d_249 (Conv3D)             (None, 8, 2, 41, 51, 442496      activation_154[0][0]             
__________________________________________________________________________________________________
batch_normalization_155 (BatchN (None, 8, 2, 41, 51, 512         conv3d_249[0][0]                 
__________________________________________________________________________________________________
conv3d_250 (Conv3D)             (None, 8, 2, 41, 51, 8320        activation_153[0][0]             
__________________________________________________________________________________________________
add_77 (Add)                    (None, 8, 2, 41, 51, 0           batch_normalization_155[0][0]    
                                                                 conv3d_250[0][0]                 
__________________________________________________________________________________________________
activation_155 (Activation)     (None, 8, 2, 41, 51, 0           add_77[0][0]                     
__________________________________________________________________________________________________
up_sampling3d_30 (UpSampling3D) (None, 8, 4, 82, 51, 0           activation_155[0][0]             
__________________________________________________________________________________________________
conv3d_251 (Conv3D)             (None, 8, 4, 82, 51, 221248      up_sampling3d_30[0][0]           
__________________________________________________________________________________________________
batch_normalization_156 (BatchN (None, 8, 4, 82, 51, 256         conv3d_251[0][0]                 
__________________________________________________________________________________________________
activation_156 (Activation)     (None, 8, 4, 82, 51, 0           batch_normalization_156[0][0]    
__________________________________________________________________________________________________
conv3d_252 (Conv3D)             (None, 8, 4, 82, 51, 110656      activation_156[0][0]             
__________________________________________________________________________________________________
batch_normalization_157 (BatchN (None, 8, 4, 82, 51, 256         conv3d_252[0][0]                 
__________________________________________________________________________________________________
conv3d_253 (Conv3D)             (None, 8, 4, 82, 51, 8256        up_sampling3d_30[0][0]           
__________________________________________________________________________________________________
add_78 (Add)                    (None, 8, 4, 82, 51, 0           batch_normalization_157[0][0]    
                                                                 conv3d_253[0][0]                 
__________________________________________________________________________________________________
activation_157 (Activation)     (None, 8, 4, 82, 51, 0           add_78[0][0]                     
__________________________________________________________________________________________________
up_sampling3d_31 (UpSampling3D) (None, 8, 8, 164, 51 0           activation_157[0][0]             
__________________________________________________________________________________________________
conv3d_254 (Conv3D)             (None, 8, 8, 164, 51 55328       up_sampling3d_31[0][0]           
__________________________________________________________________________________________________
batch_normalization_158 (BatchN (None, 8, 8, 164, 51 128         conv3d_254[0][0]                 
__________________________________________________________________________________________________
activation_158 (Activation)     (None, 8, 8, 164, 51 0           batch_normalization_158[0][0]    
__________________________________________________________________________________________________
conv3d_255 (Conv3D)             (None, 8, 8, 164, 51 27680       activation_158[0][0]             
__________________________________________________________________________________________________
batch_normalization_159 (BatchN (None, 8, 8, 164, 51 128         conv3d_255[0][0]                 
__________________________________________________________________________________________________
conv3d_256 (Conv3D)             (None, 8, 8, 164, 51 2080        up_sampling3d_31[0][0]           
__________________________________________________________________________________________________
add_79 (Add)                    (None, 8, 8, 164, 51 0           batch_normalization_159[0][0]    
                                                                 conv3d_256[0][0]                 
__________________________________________________________________________________________________
activation_159 (Activation)     (None, 8, 8, 164, 51 0           add_79[0][0]                     
__________________________________________________________________________________________________
conv3d_257 (Conv3D)             (None, 8, 8, 164, 51 1056        activation_159[0][0]             
__________________________________________________________________________________________________
conv3d_258 (Conv3D)             (None, 8, 8, 164, 51 2595        conv3d_257[0][0]                 
==================================================================================================
Total params: 1,302,147
Trainable params: 1,300,867
Non-trainable params: 1,280
