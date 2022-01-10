## React Native Reanimated 2 - Collapsing Header + FlatList Tips

Recently, I have been trying to animate a [dynamic header like AirBnb](https://blog.andreizgirvaci.com/bloglog-3) has using React Native Reanimated 2.

# The Problem

While I have successfully managed to make it work on iOS, on Android it turned out to be quite laggy and something didn't seem right. I described more in detail the bug [here](https://blog.andreizgirvaci.com/react-native-reanimated-is-being-a-turd-on-android).

# Solution (Part 1)

Luckily, I managed to fix it today following this tutorial:

%[https://medium.com/@habibridho/implementing-collapsing-toolbar-using-react-native-4a84e1718f11]

Basically, the fix was to make the header `absolute`, but at the same time, I also needed to make sure the `FlatList` is displayed properly because of that. An easy fix is to add a `marginTop: HEADER_HEIGHT` in the `FlatList`, but because my header changes its height dynamically, using a margin didn't work.

Instead, I had to use `paddingTop: HEADER_HEIGHT`, but now another problem arises, if you have a pull to refresh feature on your `FlatList` it will be hidden by the header on both iOS and Android.

# Solution (Part 2)

To fix that, you need to add a few more props to the `FlatList` and make sure `paddingTop` is only applied on Android:

* [contentInset](https://reactnative.dev/docs/scrollview#contentinset-ios) - iOS
* [contentOffset](https://reactnative.dev/docs/scrollview#contentoffset)
* [progressViewOffset](https://reactnative.dev/docs/flatlist#progressviewoffset-android) - Android

```jsx
const HEADER_HEIGHT = 50;

<FlatList
  contentContainerStyle={
    paddingTop: Platform.OS === 'android' ? HEADER_HEIGHT : 0
  }
  contentInset={{ top: HEADER_HEIGHT }}
  contentOffset={{
    y: Platform.OS === 'ios' ? -HEADER_HEIGHT : 0
  }}
  progressViewOffset={ HEADER_HEIGHT }
/>
```

Related: https://stackoverflow.com/a/63258603

# Aditional

❗️If you are passing the `contentOffset` from `FlatList` to your Header in order to animate it, you will have to make sure that `y` will take into account the `contentOffset` we have added conditionally based on the Platform like so:

```jsx
const HEADER_HEIGHT = 50;
const TRANSLATION_Y_OFFSET = Platform.OS === 'ios' ? HEADER_HEIGHT : 0;

const translationY = useSharedValue(0);

const scrollHandler = useAnimatedScrollHandler((event) => {
  translationY.value = event.contentOffset.y + TRANSLATION_Y_OFFSET;
});

<FlatList
  contentContainerStyle={
    paddingTop: Platform.OS === 'android' ? HEADER_HEIGHT : 0
  }
  contentInset={{ top: HEADER_HEIGHT }}
  contentOffset={{ y: -TRANSLATION_Y_OFFSET }}
  progressViewOffset={ HEADER_HEIGHT }
  onScroll={ scrollHandler }
/>
```

Now, this will make sure that `translationY` will always start at `0` even if we have `contentOffset` set to a different value on iOS.

# Conclusion

Animating collapsable headers in React Native is not an easy task, especially if you have a `FlatList` that has a **pull to refresh** option.

Luckily, there are ways to make it work, but you will have to go down the rabbit hole and make sure that you understand how your solution works.

Well, I hope you found this article helpful and found the answer to your question. Let me know if you encountered a similar problem in React Native and share with me if you managed to solve it in a better way. Would love to know!

Until then, see you tomorrow! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*