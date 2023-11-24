# TEMPLATE - Weather API Consumption

This template is the implementation of the [WEGnology Walkthrough](https://docs.app.wnology.io/getting-started/walkthrough/#wegnology-walkthrough), our initial step-by-step guide. In this walkthrough, a guide is provided on how to develop a weather station on the platform using data from an external API.

## Description

In a real implementation, you would use sensors and hardware to capture weather information and send this data to WEGnology using MQTT or HTTP. For this template, instead of real hardware, we use the OpenWeather API to simulate the hardware that sends weather data. This way, even without any physical devices, it is possible to experiment with various functions of the WEGnology Platform.

This template is a weather station that temporarily monitors the weather of a location with information provided by the [OpenWeather](https://openweathermap.org/) API. The data is requested periodically through the Weather Grabber WORKFLOW and stored in the Weather DEVICE. These recorded data are then presented on the Weather Station DASHBOARD.

## Key Components

- **DEVICE** *Weather*: In this application, the device is responsible for storing the weather data obtained by the workflow and serves as a reference for the blocks on the dashboard;
- **WORKFLOW** *Weather Grabber*: This is the part that makes the HTTP request and informs the received data to the attributes of the Weather DEVICE. It communicates with the API through the NODE "Fetch data". The service link containing the access key and the location to be monitored is provided in this node. These values are stored in global variables that can be easily changed at any time. Pay attention to the "Configuration" section to learn how to change them. **Must be enabled by the user**;
- **DASHBOARD** *Weather Station*: It is on the dashboard that the information received by the workflow will be presented. Each block needs to reference the corresponding attribute of the device. For example, to show the temperature, the block needs to reference the temp attribute;

## Configuration

1. Some services require appropriate permission to be used. In the case of this template, sign up on [OpenWeather](https://home.openweathermap.org/users/sign_up) to obtain the access key;
2. Once registered, get your API key:
    - Click on your username;
    - Choose the "My API Keys" option;
    - Copy your key and save it in an easily accessible place, as it will be used in the following steps.
3. Navigate to Application Globals to change the values of global variables:
    - Select the "gps_location" variable and enter the latitude and longitude of the location you want to monitor in the "value" field;
    - Repeat the same process for the "api_key" variable and paste the key obtained in step 2 into the "value" field.
4. Enable the Weather Grabber WORKFLOW, to do this, just click on the word "Enable" in the notice located in the bottom right corner of the screen.

After completing the configurations, the workflow will send weather updates about the specified location every 10 minutes (this time can be changed in the "Timer" block). The data will be stored in the Weather DEVICE and can be viewed through the Weather Station DASHBOARD.

## Auxiliary Documentation

- See all the development steps of this template in the [WEGnology Walkthrough](https://docs.app.wnology.io/getting-started/walkthrough/#wegnology-walkthrough).
- OpenWeather is an API that provides weather data in a simple way. This service, despite being paid, has a very generous free plan that provides 1,000,000 calls monthly and up to 60 per minute. Check the [price table](https://openweathermap.org/price) if you want more details about the plans or access its [documentation](https://openweathermap.org/current) to learn more about this API.

## About

This template is in version 1.0.0.

For any questions, we recommend using the [forum](https://forums.app.wnology.io/).

Copyright © 2023 WEG SA. All rights reserved.

Licensed under the MIT license.

[https://www.weg.net](https://www.weg.net)
