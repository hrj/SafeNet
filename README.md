# A URL fetch service
... for Android.

# For users
This will be an Android app, that will let other applications get data from the Internet. The advantages are:

  * Fewer applications will need to have permission to access the Internet and read / write to SD card, which means better security.
  * You will be able to log the Internet accesses made by these applications.
  * You will be able to disable some applications from making requests, to save bandwidth, for example.


# For developers
Your app will be able to... 

  * fetch data from the Internet without requiring the Internet permission.
  * initiate a large file download without needing permission to access the SD card.
  * schedule a URL fetch for later based on some condition. For example, when a network connection becomes available. Hence, it won't need permissions to know the current WiFi state, etc.

Because of these fewer permissions, users can trust your application more.

There will be a library API to handle communication with the service. And to give you maximum freedom, there will be two versions of the library. One which works as advertised above, and another which issues the HTTP fetch directly (without using the service). Both the libraries will have the same API, so, at anytime you will be to switch between the two without changing a single line of code.

## How does it work
This will be a simple app which accepts URL fetch requests from other applications and fetches them (HTTP GET) from the internet as a background service. Upon completion, the data can be returned to the application as a byte stream. The data may be saved to the SD card if it is marked as a large download.

Since this is based on a callback, the network need not be available at all times. The service will (optionally) queue the request and fetch whenever a network is available.

Another useful feature would be avoiding duplicate requests. For example, an app may want to fetch some data periodically, say every two hours. But if the network is not available for two days, then only one request should be made when the network becomes available, not 50! This could be done by letting the app assign a unique id to the request. Requests that have the same id will over-write other requests from the same app with the same id.

## Logging and Filtering
From the user point of view, there is tremendous advantage in having a centralized URL Fetcher, because she will be able to Log the requests that go through it, and also filter some requests. For example, she could filter an app that she doesn't want to be updated (for whatever reason).

## Distribution
The app will be open-source and made available on all App markets and also as a direct APK download.

The only hurdle to this idea that I can see is that the app will have to be installed separately by the user. The problem will be reduced over time as more and more apps use this service. So the chances of the app being already present will increase. Also, custom ROMs might pre-package this app, so it will be present by default.

The project is under development. Watch this space for updates.