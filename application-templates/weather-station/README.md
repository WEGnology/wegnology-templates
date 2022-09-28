# Weather Station
This template provides a complete implementation of the [WEGnology Walkthrough](https://docs.app.wnology.io/getting-started/walkthrough/). Weather data is periodically requested from an external API and recorded to a [WEGnology Device](https://docs.app.wnology.io/devices/overview/). The recorded weather data is then presented on your own personal weather dashboard.

## Setup
1. Navigate to your [Application Globals](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationWeatherStation-0~/globals) and configure the following fields:
	1. `gps_location`: Location (latitude, longitude) that will be used when requesting weather data.
	1. `api_key`: OpenWeatherMap API key. [OpenWeatherMap](https://openweathermap.org/api) is a separate, paid service, that you sign up for. They provide a free tier, which offers plenty of resources for this application.
2. Enable the [Weather Grabber](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationWeatherStation-0~/workflows/~exportplaceholderid-flow-weatherGrabber-0~/develop) workflow.

## Weather Grabber Workflow
The [Weather Grabber](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationWeatherStation-0~/workflows/~exportplaceholderid-flow-weatherGrabber-0~/develop) workflow has a timer that runs every two minutes to request weather data from the OpenWeatherMap API. It uses the API key and location that you configured above.

## Weather Station Dashboard
The [Weather Station](https://console.app.wnology.io/dashboards/~exportplaceholderid-dashboard-weatherStation-0~) dashboard displays a variety of live and historical weather data. This data is displayed from the [Weather](https://console.app.wnology.io/applications/~exportplaceholderid-application-applicationWeatherStation-0~/devices/~exportplaceholderid-device-weather-0~) device, which is updated by the Weather Grabber workflow.

## Resources
The following resources offer further details on implementing this template:

* [WEGnology Walkthrough](https://docs.app.wnology.io/getting-started/walkthrough)
* [Workflows](https://docs.app.wnology.io/workflows/overview/)
* [Devices](https://docs.app.wnology.io/devices/overview/)
* [Dashboards](https://docs.app.wnology.io/dashboards/overview/)

---

This template was created by WEGnology. If you have general questions or comments, let us know on the [WEGnology Forums](https://forums.app.wnology.io).

Copyright (c) 2022 WEGnology.