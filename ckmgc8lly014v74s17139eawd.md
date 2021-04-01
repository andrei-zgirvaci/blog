## The fastest way to build a React Native App! 🚀

I have been building React Native apps for more than 3 years now and I think finally I found the fastest way to build an MVP that looks sick and at the same time doesn't take months to design.

### 1. Starting out
For my first app that I worked on, I used  [react-native-elements](https://reactnativeelements.com/) in order to build components, such as Buttons, Icons, Forms, etc...

At the start, I was moving fast as I was using most of the built-in components, but what I found out, was that as more the app progressed, the more it became the need to create custom components instead, as there were always use cases when the built-in components will lack something or won't match my overall design.

### 2. Building my own components

Later on, I thought that maybe it's better to not use any UI libraries at all and just build my own components as it was not that hard and would be less frustrating as I wouldn't have to understand the specific UI library props and how to design their components.

This might be a good idea when the project becomes big, but when building an MVP, you don't have much time. You want to build something fast, but also *keep the doors open* in case the project scales fast, you will be able to adjust the components to your brand design quickly.

And this finally leads to my perfect solution so far...

### 3. UI Kitten + tailwind-rn = 🚀

#### UI Kitten 🎨

Almost a year ago, I discovered a UI library called  [UI Kitten](https://akveo.github.io/react-native-ui-kitten/). First, their landing page looks great! Second, their components look sexy as hell! 🕺

Not only that, but they also support an easy way to  [customize](https://akveo.github.io/react-native-ui-kitten/docs/design-system/eva-design-system-intro#eva-design-system)  your components, colors and theme.

The latter option is very important as you can start building your app with their design theme and colors and not worry about spending a lot of time coming up with your own design. And once your app scales and you find the need to go the extra mile and customize your colors, shadows, buttons, etc. You can easily do that using by creating a  [custom mapping](https://akveo.github.io/react-native-ui-kitten/docs/design-system/customize-mapping#customize-component-mapping).

Wait, things get even better!

#### Tailwind 🦎

Everyone, welcome tailwind for React Native! -  [tailwind-rn](https://github.com/vadimdemedes/tailwind-rn) 👏

In one of my  [previous posts](https://blog.andreizgirvaci.com/using-tailwind-in-react-native), I talked about my experience with tailwind-rn and how amazing I feel having this kind of power in React Native.

But, there is a small issue that still needs to be fixed.

You see, UI Kitten and Tailwind have by default different colors and there are gonna be use cases when you need to add a background color to your `View`, but you want it to also match the button color from the UI Kitten built-in component.

Luckily, UI Kitten matches the tailwind's  [color scheme](https://colors.eva.design/)  structure pretty well and that makes them both integrate very well with each other!

#### Configuring UI Kitten to work with Tailwind 🔨

Bellow, I attached a quick way to import colors from tailwind so UI Kitten can use them instead. I take advantage of the `getColor` method that `tailwind-rn` exposes which saves us a lot of time as we would have to copy-paste all those colors into the theme. Moreover, we would have to change them constantly if we decide to update the Tailwind config.

First, we have to create a file where we are gonna store the UI Kitten theme config, like so:

```jsx
/* eva-theme.js */

import * as eva from '@eva-design/eva';
import { getColor } from 'tailwind-rn';

const colors = {
  'color-primary-100': getColor('blue-100'),
  'color-primary-200': getColor('blue-200'),
  'color-primary-300': getColor('blue-300'),
  'color-primary-400': getColor('blue-400'),
  'color-primary-500': getColor('blue-500'),
  'color-primary-600': getColor('blue-600'),
  'color-primary-700': getColor('blue-700'),
  'color-primary-800': getColor('blue-800'),
  'color-primary-900': getColor('blue-900'),

  'color-success-100': getColor('green-100'),
  'color-success-200': getColor('green-200'),
  'color-success-300': getColor('green-300'),
  'color-success-400': getColor('green-400'),
  'color-success-500': getColor('green-500'),
  'color-success-600': getColor('green-600'),
  'color-success-700': getColor('green-700'),
  'color-success-800': getColor('green-800'),
  'color-success-900': getColor('green-900'),

  'color-warning-100': getColor('yellow-100'),
  'color-warning-200': getColor('yellow-200'),
  'color-warning-300': getColor('yellow-300'),
  'color-warning-400': getColor('yellow-400'),
  'color-warning-500': getColor('yellow-500'),
  'color-warning-600': getColor('yellow-600'),
  'color-warning-700': getColor('yellow-700'),
  'color-warning-800': getColor('yellow-800'),
  'color-warning-900': getColor('yellow-900'),

  'color-danger-100': getColor('red-100'),
  'color-danger-200': getColor('red-200'),
  'color-danger-300': getColor('red-300'),
  'color-danger-400': getColor('red-400'),
  'color-danger-500': getColor('red-500'),
  'color-danger-600': getColor('red-600'),
  'color-danger-700': getColor('red-700'),
  'color-danger-800': getColor('red-800'),
  'color-danger-900': getColor('red-900'),
};

export default {
  ...eva.light,
  ...colors,
};
```

I haven't defined all the colors as I don't use them at the moment, but you are free to do so if you find it necessary. Make sure to follow the official  [documentation](https://akveo.github.io/react-native-ui-kitten/docs/design-system/design-system-theme#a-theme).

Next, we need to import the theme into our `AplicationProvider`:

```jsx
import React from 'react';
import * as eva from '@eva-design/eva';
import { ApplicationProvider, IconRegistry } from '@ui-kitten/components';
import { EvaIconsPack } from '@ui-kitten/eva-icons';
import { StatusBar } from 'expo-status-bar';

import customMapping from '../config/eva-mapping';
import customTheme from '../config/eva-theme';
import Navigation from './navigation';

export default function App() {
  return (
    <>
      <IconRegistry icons={EvaIconsPack} />
      <ApplicationProvider
        {...eva}
        theme={customTheme}
        customMapping={customMapping}
      >
        <StatusBar backgroundColor="#fff" style="dark" />
        <Navigation />
      </ApplicationProvider>
    </>
  );
}
```

And that's it! 👏 Now you should have your Tailwind colors imported to UI Kitten! Sweet 👌

### Conlusion

I have been using UI Kitten for already 3 MVP apps, 2 of them became full-scale apps and one is still in the works at the moment. So far, I haven't had any issues with this UI library and I am super happy with it! My productivity skyed rocketed as I can focus on more important things and less on building essential components from scratch.

Now, that I have a new tool in my toolbelt (tailwind-rn), I can move even faster by using the utility first approach while styling custom components. I hope you do too 🙃

<br />

That's it for today friends! I hope you found this article useful. Until then, have an amazing rest of your day! See you next week! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*

 