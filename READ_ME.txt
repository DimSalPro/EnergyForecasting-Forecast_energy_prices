Create a virtual environment by following the instructions at howto.txt file. 
Note that these instructions apply for Linux.

Open a Terminal and execute the following command to run the program
python3 forecasting_main.py

Several parameters can be changed from pipeline.config
===================================================================================================================================================
More specifically,

"high_correlated_features": true/false , to activate / disactivate the option of high correlated features (default: true) | type: boolean
"show_plots": true / false, to activate / disactivate the option of showing the plots (default: false) | type: boolean
"save_plots": true / false, to activate / disactivate the option of saving the plots (default: true) | type: boolean
"use_only_correct_data": true / false, use as data some specific timestamps where the data has the sensors worked as good as possible (default: true) | type: boolean
"fix_if_sensor_restart": true / false, use the function that fixes the data if a sensor restart took place - can only be applied in site 22 - (default: false) | type: boolean
"save_predictions": true / false, specify if you want to save the predictions in a csv file (default: true) | type: boolean
"choose_model_to_run": select the desired machine learning model for the forecasting (options: "regression", "recurrent_neural_network", "arima", "sarimax", "fb_prophet") | type: str
"save_evaluation": true / false, specify if you want to save the evaluation metrics in a csv (default: true) | type: boolean
"good_time_start": specify the starting timestamp for the use_only_correct_data time window (default: "2019-09-06T00:00:00Z") | type: str
"good_time_end": specify the ending timestamp for the use_only_correct_data time window  (default: "2021-08-05T00:00:00Z") | type: str
"path_to_energy_data": specify the path along with the name of the json file containing the energy data retrieved from the sensor | type: str
                       example: "site2_energy2.json"
"path_to_power_data": specify the path along with the name of the json file containing the power data retrieved from the sensor | type: str
                      example: "site2_power2.json"
"path_to_temp_humi_data": specify the path along with the name of the json file containing the weather data retrieved from the sensor | type: str
                          example: "site2_temp_humi2.json"
"path_to_weather_data": specify the path along with the name of the csv file containing the weather data retrieved utilizing WorldWeather librar | type: str
                        (see: https://github.com/David-Woroniuk/WorldWeatherPy)
                        example: "Athens_hourly_weather.csv"
"scaler": specify the scaler that will scale the data in the RNN and regression models (options: "standard", "minmax") | type: str



For the different machine learning models, one can adjust the following parameters
All the available parameters for each model are in the configuration file (change only what is possible for each model)
---------------------------------------------------------------------------------------------------------------------------------------------------- 
"test_size": number of days for which the energy consumption will be forecasted (default: 7) | type: int
"epochs": number of epochs for model to train | type: int
"batch_size": batch size for the model to train | type: int
"only_energy": true / false, use only the energy data values - not any other datum from the dataset - (default: false) | type: boolean
"exogeneous_data": true / false , to activate / disactivate the option of the exogeneous data addition, in this case weather data, for the sarimax model (default: false) | type: boolean
"grid_search_for_order_params": true / false , to activate / disactivate the option of grid search for the hyperparameters (p, d, q) the sarimax model (default: false) | type: boolean
"add_holidays": true / false, to activate / disactivate the option of adding holidays for the fb_prophet model (default: false) | type: boolean
"optimizer": change the optimizer of the model (options: "adam", "adamax", "adadelta", "adagrad", "rmsprop", "sgd") | type: str
"period": the number of periods before that most affect the fb_prophet training (default: 1) | type: int
"fourier_order": the fourier parameter of the fb_prophet model (set to higher if many fluctuations during a period in data) (default: 8) | type: int

