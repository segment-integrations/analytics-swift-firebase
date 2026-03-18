# Analytics-Swift Firebase (Fork)

> **This is a fork of [segment-integrations/analytics-swift-firebase](https://github.com/segment-integrations/analytics-swift-firebase)** updated to support **Firebase Apple SDK 12.x**.

Add Firebase device mode support to your applications via this plugin for [Analytics-Swift](https://github.com/segmentio/analytics-swift)

## Changes from upstream

- Updated Firebase dependency from `~> 11.x` to `>= 12.0.0`
- Replaced `import Firebase` with `import FirebaseCore` (recommended for Firebase 12+)
- Bumped `swift-tools-version` to 5.9

## Adding the dependency

***Note:** the Firebase library itself will be installed as an additional dependency.*

### via Xcode
In the Xcode `File` menu, click `Add Packages`.  You'll see a dialog where you can search for Swift packages.  In the search field, enter the URL to this repo.

https://github.com/sSahad/analytics-swift-firebase

You'll then have the option to pin to a version, or specific branch, as well as which project in your workspace to add it to.  Once you've made your selections, click the `Add Package` button.

### via Package.swift

Open your Package.swift file and add the following to your the `dependencies` section:

```swift
.package(
    url: "https://github.com/sSahad/analytics-swift-firebase.git",
    branch: "main"
),
```

*Note the Firebase library itself will be installed as an additional dependency.*


## Using the Plugin in your App

Open the file where you setup and configure the Analytics-Swift library.  Add this plugin to the list of imports.

```swift
import Segment
import SegmentFirebase // <-- Add this line
```

Just under your Analytics-Swift library setup, call `analytics.add(plugin: ...)` to add an instance of the plugin to the Analytics timeline.

```swift
let analytics = Analytics(configuration: Configuration(writeKey: "<YOUR WRITE KEY>")
                    .flushAt(3)
                    .trackApplicationLifecycleEvents(true))
analytics.add(plugin: FirebaseDestination())
```

Your events will now begin to flow to Firebase in device mode.


## License
```
MIT License

Copyright (c) 2021 Segment

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
