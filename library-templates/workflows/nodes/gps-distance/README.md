# GPS Distance

Calculates the distance, in meters, between two GPS coordinates.

Once imported, this node is available in your application's collection of [Custom Nodes](https://docs.app.wnology.io/workflows/custom-nodes/overview/).

## Input Configuration

* `Starting GPS Point`: Starting GPS coordinate in any [supported format](https://docs.app.wnology.io/devices/state/#gps-attributes).
* `Ending GPS Point`: Ending GPS coordinate in any [supported format](https://docs.app.wnology.io/devices/state/#gps-attributes).

## Output Result

The output is the distance between the starting and ending GPS points, in meters. If either GPS coordinate is invalid, the result will be `null`.

## License

Copyright (c) 2022 WEGnology. All rights reserved.

Licensed under the [MIT](https://github.com/WEGnology/wegnology-templates/blob/master/LICENSE.txt) license.