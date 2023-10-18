# Analogue-Nowcasting-Model
## Table of Contents
- [Proposal](#Proposal)
- [Reference Papers](#Papers)
- [Data](#Data)
- [Contribute](#contribute)
- [Credits](#credits)
- [License](#license)

## Proposal
- [Proposal for the development of a data driven model for rainfall forecasting.docx](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981503/Proposal.for.the.development.of.a.data.driven.model.for.rainfall.forecasting.docx)

## Papers 
- [An Analog Forecast System for Precipitation Forecasting.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981265/An.Analog.Forecast.System.for.Precipitation.Forecasting.pdf)

- [Enhanced Analogue Forecast System for Precipitation by Autoencoder Feature Extraction.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981267/Enhanced.Analogue.Forecast.System.for.Precipitation.by.Autoencoder.Feature.Extraction.pdf)

- [An analogy based method for strong convection forecasts in China using GFS forecast data.pdf](https://github.com/yh115/Analogue-Nowcasting-Model/files/12981270/An.analogy.based.method.for.strong.convection.forecasts.in.China.using.GFS.forecast.data.pdf)


## Data
Data Details
Source: ECMWF ERA5 dataset.
Time Interval: Hourly.
Resolution: 0.25° x 0.25°.
Parameters: 
•	Geopotential height: 925hPa, 850hPa, 700hPa.
•	Wind vectors: 925hPa, 850hPa, 700hPa.
•	Vapour Flux: 925hPa.
•	Relative humidity: 850hPa and 700hPa
Region: 95E - 120E longitude and 5S - 15N latitude.

https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-pressure-levels?tab=form
<pre>
```python
def function():
    pass
```
</pre>
Inline Code: Use single backticks (`) before and after the inline code.

Remember, the key is clarity. Use visuals, be concise, and organize the content logically. Always think from the perspective of someone who's seeing your project for the first time.




User
How to upload my word file?

ChatGPT
To upload a file (e.g., a Word document) to GitHub, you'll need to use Git commands if you're working from the command line, or you can use GitHub's web interface. Here's how to do it using both methods:

1. Using GitHub's Web Interface:
Navigate to Your Repository: Go to GitHub and open the repository where you want to upload the file.
Upload Files: Click on the "Add file" button (usually near the right side of the screen) and select "Upload files" from the dropdown.
Drag & Drop or Choose File: You can drag and drop the Word file into the box or click "choose your files" to open a file picker and select your file.
Commit: Scroll down to find the "Commit changes" section. Add a brief message describing the upload, then click on the "Commit changes" button.
2. Using Git from the Command Line:
Navigate to Your Local Repository: On your local machine, open the terminal or command prompt and navigate to your cloned repository.

Copy the File: Copy the Word file to the repository's directory.

Add the File to the Repository:

bash
Copy code
git add yourfile.docx
Commit the Addition:

bash
Copy code
git commit -m "Added Word file"
Push to GitHub:

bash
Copy code
git push origin main
Replace main with the appropriate branch name if you're not using the default branch.







