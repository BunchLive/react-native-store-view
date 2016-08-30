# ReactNativeStoreView

[![CI Status](https://travis-ci.org/rh389/react-native-store-view.svg?branch=master)](https://travis-ci.org/rh389/react-native-store-view)

## Installation

Fetch the package using npm:

```
npm install --save react-native-store-view
```

Then add `pod 'ReactNativeStoreView', :path => '../node_modules/react-native-store-view'` to your project's `Podfile`,
modifying the path as necessary.

Finally, run `pod install` from the command line to link the pod to your xcode project.

## Example usage

```
import React, {Component} from "react";
import {Text, View, TouchableHighlight} from "react-native";
import StoreViewManager from "react-native-store-view";

class ReactNativeStoreViewExample extends Component {
  render() {
    return (
      <View>
        <TouchableHighlight onPress={this.onPressButton}>
          <Text>
            Tap here to open the app store
          </Text>
        </TouchableHighlight>
      </View>
    );
  }

  onPressButton() {
    StoreViewManager.loadProductWithParameters({
      iTunesItemIdentifier: 364709193 //The only mandatory parameter is a numeric App Store ID. This one is iBooks.
      //, affiliateToken: 'string'
      //, campaignToken: 'string'
      //, providerToken: 'string'
    })
      .then(() => {
        console.log('SKStoreProductViewController successfully loaded the product over the net, but is not yet displaying anything');
        StoreViewManager.presentViewController();
      })
      .then(() => {
        console.log('SKStoreProductViewController is now modal. When it is dismissed, we\'ll return to this view.');
      })
      .catch((err) => {
        console.error(err);
      });
  }
}
```

See the `ReactNativeStoreViewExample` project for more.

## Known limitations
`SKStoreProductViewController` is *not supported* for use in a simulator environment, and so neither is this module. You'll need to test your application using a real device.

## License

ReactNativeStoreView is available under the MIT license. See the LICENSE file for more info.
