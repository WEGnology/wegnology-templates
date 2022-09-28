# Blob Data Simulator

This template demonstrates:
- How to simulate [blob attribute data](https://docs.app.wnology.io/devices/blobs/) via a [workflow](https://docs.app.wnology.io/workflows/overview/) 
- How to save that data to [device state](https://docs.app.wnology.io/devices/state/)
- How to use that device state in a [dashboard](https://docs.app.wnology.io/dashboards/overview/)

## Dependencies

This component has no additional WEGnology dependencies.

## Usage

After you have added the template to your application, visit your application's [workflows list](/applications/recent/workflows) and enable the "Blob Simulator" workflow.

### Simulator Workflow 

By default, the included workflow runs once every minute. You can change this by updating the [Timer Trigger](https://docs.app.wnology.io/workflows/triggers/timer/) to a frequency of your choosing. The workflow may also be run manually by pressing the [Virtual Button Trigger](https://docs.app.wnology.io/workflows/triggers/virtual-button/).

The workflow requests a random image from [Lorem Picsum](https://picsum.photos/), a free service that returns placeholder images given a URL you generate. The [Random Number Node](https://docs.app.wnology.io/workflows/logic/random-number/) in the workflow is responsible for randomizing a section of the URL to return a new image with each request.

The [HTTP Node](https://docs.app.wnology.io/workflows/data/http/) makes the request to the service and saves the response body (a JPEG image) on the payload as a [Base64](https://developer.mozilla.org/en-US/docs/Glossary/Base64)-encoded string.

### Saving to Device State

Once the Blob Simulator workflow has retrieved and encoded the image, it writes the data as state using the [Device State Node](https://docs.app.wnology.io/workflows/outputs/device-state/) to the `image` attribute on the included `Device Recording Blob Simulator Output` device. That attribute is of the data type `blob`, and its [Content Type](https://docs.app.wnology.io/devices/blobs/#content-types) is set to `image/jpeg`, which matches the content type of the blob being written by the simulator.

### Displaying on a Dashboard

The template includes a dashboard with an [Image Block](https://docs.app.wnology.io/dashboards/image/) and an [Indicator Block](https://docs.app.wnology.io/dashboards/indicator/) for displaying the most recent image saved to the template's device.

For the Image Block, display the result by choosing the "Show image from a device attribute..." option and selecting the appropriate device and attribute.

The Indicator Block is included as a demonstration of how to render the image in [Markdown](https://daringfireball.net/projects/markdown/syntax#img) given the result of the query.

## License

Copyright (c) 2022 WEGnology. All rights reserved.

Licensed under the [MIT](https://github.com/WEGnology/wegnology-templates/blob/master/LICENSE.txt) license.