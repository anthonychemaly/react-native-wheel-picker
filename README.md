[AUTHOR]: https://github.com/rozhkovs
[FEEDBACK_GITHUB]: https://github.com/quidone/react-native-wheel-picker-feedback

# React Native Wheel Picker

A flexible React Native Wheel Picker for iOS and Android without using the native side.

<div style="display: inline-block">
  <img src="./docs/images/simple-picker-ios.gif" height="200"/>
  <div style="text-align: center;">On iOS</div>
</div>
<div style="display: inline-block">
  <img src="./docs/images/simple-picker-android.gif" height="200"/>
  <div style="text-align: center;">On Android</div>
</div>
<div style="display: inline-block">
  <img src="./docs/images/customized-picker.gif" height="200"/>
  <div style="text-align: center;">Customization</div>
</div>


## Features
 - Without native side.
 - Unified API.
 - Only native animations.
 - [Support native feedback](#Native-Feedback).
 - [Support virtualization](#withVirtualized).
 - Compatible with Expo.
 - Deep customization
 - Written ```TypeScript```.

## Installation
```shell
yarn add @quidone/react-native-wheel-picker
```

## Navigation

- [Usage](#Usage)
- [Native Feedback](#Native-Feedback)
- [API](#API)
  - [WheelPicker](#WheelPicker)
  - [usePickerItemHeight](#usePickerItemHeight)
  - [useScrollContentOffset](#useScrollContentOffset)
  - [withVirtualized](#withVirtualized)
- [Footer](#-Author)

## Usage

If you want to see more examples and experiment, run the examples locally.

```shell
git clone git@github.com:quidone/react-native-wheel-picker.git
cd react-native-wheel-picker
yarn install
cd example && yarn install && yarn ios
```

### Simple case

```jsx
import React, {useState} from 'react';
import WheelPicker from '@quidone/react-native-wheel-picker';

const data = [...Array(100).keys()].map((index) => ({
  value: index,
  label: index.toString(),
}))

const App = () => {
  const [value, setValue] = useState(0);
  return (
    <WheelPicker
      data={data}
      onValueChanged={({item: {value}}) => setValue(value)}
    />
  );
};

export default App;
```

## Native Feedback

You can trigger native sound and impact with [@quidone/react-native-wheel-picker-feedback][FEEDBACK_GITHUB]
and onValueChanging event

```jsx
// ...
import WheelPickerFeedback from '@quidone/react-native-wheel-picker-feedback';

const App = () => {
  return (
    <WheelPicker
      onValueChanging={() => {
        WheelPickerFeedback.getSoundAndImpact();
      }}
    />
  );
};
```

## API

### WheelPicker

#### Props
- ```data``` [array] - items of picker
- ```value?``` [any] - current value of picker item
- ```itemHeight?``` [number] - height of picker item in the center.
- ```width?``` [number | string] - width of picker.
- ```onValueChanging?``` [function] - An event that is triggered when the value is changing.
- ```onValueChanged?``` [function] - An event that is triggered when the value is changed (wheel is stopped and no touch).
- ```keyExtractor?``` [function] - key extractor from picker item.
- ```renderItem?``` [function] - render picker item content.
- ```renderItemContainer?``` [function] - render picker item container (there is animated container).
- ```renderOverlay?``` [function | null] - render overlay over the picker.
- ```renderList?``` [function] - render list (Advanced, It is not recommended to use).
- ```style?``` [object | array] - root style.
- ```itemTextStyle?``` [object | array] - item text style for picker item.
- ```selectionOverlayStyle?``` [object | array] - style for the overlay element in the center
- ```scrollEventThrottle?``` [object | array] - [original](https://reactnative.dev/docs/scrollview#scrolleventthrottle-ios)


### usePickerItemHeight
This hook returns the item height which was passed via props.

### useScrollContentOffset
This hook returns the animated value of the ScrollView offset.

### withVirtualized
This HOC returns virtualized picker

```jsx
import WheelPicker, {withVirtualized} from '@quidone/react-native-wheel-picker';

const VirtualizedWheelPicker = withVirtualized(WheelPicker);
```

#### Additional props
- ```initialNumToRender?``` (default = 3) - [original](https://reactnative.dev/docs/flatlist#initialnumtorender).
- ```maxToRenderPerBatch?``` (default = 3) - [original](https://reactnative.dev/docs/flatlist#maxtorenderperbatch).
- ```windowSize?``` - [original](https://reactnative.dev/docs/flatlist#windowsize).
- ```updateCellsBatchingPeriod?``` (default = 10) - [original](https://reactnative.dev/docs/flatlist#updatecellsbatchingperiod).

## 👨‍💻 Author
[Sergey Rozhkov][AUTHOR]

## 🎯 Was it helpful?
Do you like it and find it helpful? You can help this project in the following way:
- ⭐ Put the star.
- 💡 Suggest your ideas.
- 😉 Open a founded issue.

## 🤝 Contributing
See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## 📄 License
Quidone React Native Wheel Picker is MIT licensed, as found in the [LICENSE](LICENSE) file.

---

Made with [create-react-native-library](https://github.com/callstack/react-native-builder-bob)
