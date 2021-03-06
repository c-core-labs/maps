# Getting Started

Congratulations, you successfully installed react-native-mapbox/maps! 🎉  
Where to go from here?  
You can head straight to [examples](/example) folder if you want to jump into the deep end.  
However, if you prefer an easier ramp-up, then make sure to stick around and check out the guides below.

## Setting your accessToken

In order to work, mapbox requires you to create an accessToken and set it in your app.  
If you haven't created on yet, make sure to sign up for an account [here](https://www.mapbox.com/signup/)  
You can create and manage your access tokens on your [Mapbox Account page](https://www.mapbox.com/account/)  
Once you have your accessToken, set it like this

```js
import MapboxGL from "@react-native-mapbox/maps";

MapboxGL.setAccessToken("<YOUR_ACCESSTOKEN>");
```

## Disabling Telemetry

By default mapbox collects telemetry.
If you would like to programmatically disable this within your app add the code below.

Notice that `isTelemetryEnabled` returns a Promise.

```js
  componentDidMount() {
    MapboxGL.isTelemetryEnabled().then(isEnabled => {
      isEnabled && MapboxGL.setTelemetryEnabled(false);
    });
  }
```

For more information on mapbox and telemetry: [https://www.mapbox.com/telemetry](https://www.mapbox.com/telemetry)

## Show a map

```js
import React, { Component } from "react";
import { StyleSheet, View } from "react-native";
import MapboxGL from "@react-native-mapbox/maps";

MapboxGL.setAccessToken("<YOUR_ACCESSTOKEN>");

const styles = StyleSheet.create({
  page: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "#F5FCFF"
  },
  container: {
    height: 300,
    width: 300,
    backgroundColor: "tomato"
  },
  map: {
    flex: 1
  }
});

export default class App extends Component {
  componentDidMount() {
    MapboxGL.isTelemetryEnabled().then(isEnabled => {
      isEnabled && MapboxGL.setTelemetryEnabled(false);
    });
  }

  render() {
    return (
      <View style={styles.page}>
        <View style={styles.container}>
          <MapboxGL.MapView style={styles.map} />
        </View>
      </View>
    );
  }
}
```
