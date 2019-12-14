# DC_Scooters
For a final project in URPL-GP-1620 - Spatial Analysis and Visualization at NYU Wagner, I decided to explore DC Scooters. Due to the lack of available dataset, I created my own by calling the Dockless Vehicle APIs (available at https://ddot.dc.gov/page/dockless-api) five times a day for about a week. 

This documentation will primarily discuss how I created “dc_scooter_data.csv,” but I have also uploaded the dataset with DC Ward location added.  

## Data Gathering Process
Starting November 14, 2019, I began calling the following Dockless Vehicle APIs and downloading the returned json file:
*	Bird - https://gbfs.bird.co/dc
*	Bolt - https://www.bolt.miami/bolt2/dc/gbfs/en/free_bike_status.json
*	Jump Scooters - https://gbfs.uber.com/v1/dcs/free_bike_status.json
*	Lime - https://lime.bike/api/partners/v1/gbfs/free_bike_status.json
*	Lyft - https://s3.amazonaws.com/lyft-lastmile-production-iad/lbs/dca/free_bike_status.json
*	Skip - https://us-central1-waybots-production.cloudfunctions.net/ddotApi-dcFreeBikeStatus
*	Spin - https://web.spin.pm/api/gbfs/v1/washington_dc/free_bike_status

My analysis focuses primary in scooters, so I did not include Jump Bikes or Capital Bikeshare information. I also had problems with the Razor API so I left it out. 

From November 16th – November 22nd, I consistently downloaded the free_bike_status.json at the following times:
*	8:30AM
*	12:00PM
*	3:30PM
*	6:30PM
*	9:30PM

These times are approximations as I was downloading manually, but all were called within three minutes of the recorded time. On December 14th and 15th I did not download at consistent times. I have not filtered these days out however, because they may prove useful for some analysis. 

## Dates
All dates have been set to an ISO 8601 format, but due to issues with the times when uploaded to rstudio, I did not set the timezone. All data was downloaded post day light saving time in EST. 

## DC Ward Location
Using QGIS I joined the dc_scooter_data.csv and the Ward from 2012 dataset (found [here](https://opendata.dc.gov/datasets/ward-from-2012)). The Ward data comes with a lot of attributes beyond the name and was difficult to upload to analyze. I slimmed the initial data to just include the bike ID, latitude, longitude, company name, date and time, ward name, and ward number. This data is published as “dc_scooter_data_ward_slim.csv.” 

