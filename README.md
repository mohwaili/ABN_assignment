# Mohammed Al Waili - Implementation of the iOS assignment

This is my implementation for the ABN Amro assignment

## Wikipedia app

The Wikipedia app is extended to handle a new deeplink 'placeWithCoordinates' and I have created a new `WMFUserActivityType` called `WMFUserActivityTypePlaceWithCoordinates` which is used to handle the deeplink.  This can be found in `NSUserActivity+WMFExtensions.h & .m` files. 

## Locations app

In the `WMFAppViewController.m` I added a new case to handle the new deeplink type. The code gets the coordinates from the activity and passes it to the placesViewController using the following function `updateMapWith:coordinates`

The `Locations` app is purely written in SwiftUI. It has one screen that shows a list of locations fetched from GitHub. Each list item shows a map view, location title and coordinates. The Location item view supports voice over, RTL (Arabic), dark mode and increased font sizes.

It's also possible to search for location by swiping down to show a search field. It uses CoreLocation's `CLGeocoder` to fetch location information for a giving query. 

## Testing

The code is covered with integration tests & unit tests
The UI is covered by Snapshot tests with the following variants 

- Light mode
- Dark mode
- Extra extra extra large size category
- RTL Arabic support

I created 2 test plans, the first one uses the default configuration and the second one is created to test for RTL (Arabic) configuration 

For stubbing the data coming from GitHub, I've created a custom URLProtocol to override the responses. And for the `CLGeocoder` I created a Mock to stub the return values. 
