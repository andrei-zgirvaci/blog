## How to use TailwindCSS in React Native? 🦎

As many of you probably know, recently I  [built my portfolio website in Next.js](https://blog.andreizgirvaci.com/building-my-freelance-portfolio-in-nextjs) . For styling, I decided to try the TailwindCSS library as it's gaining quite some popularity at the moment. I was surprised at how well it played out in the end.

I enjoyed very much writing classes instead of styling my elements inline or coming up with class names for them. It increased my productivity a lot and I came to appreciate a lot the utility first approach!

But, it has to come to an end as I am a React Native and I will have to go back to write inline styles, or do I? I might not!

As I am starting [my new startup](https://blog.andreizgirvaci.com/starting-my-new-startup)  now, I always like to try new things and learn from past experience. What I learned from my past projects, is that I don't like the way I style my components, would that be storing my styles outside the components or doing inline styles or doing both, it doesn't compare to how much faster I use to build components with Tailwind.

That's what made me start to search through google repositories for styling libraries. I found a few libraries that try to change the way we style components in React Native:
- https://github.com/Shopify/restyle
- https://github.com/robinpowered/glamorous-native
- https://github.com/tachyons-css/react-native-style-tachyons

I went through all of them, but It still didn't feel right. What I found later was: https://github.com/vadimdemedes/tailwind-rn and this one really resonated with me! 😊

It's basically Tailwind, but made compatible with React Native! Today, was my first day trying it in an actual project, so I am gonna see how it works out, but so far, I enjoy it! 👏

Of course, there are gonna be cases when I am gonna reuse styles in different components, but for that, I am gonna just do this:

```jsx
import { StyleSheet } from 'react-native';
import tailwind from 'tailwind-rn';

export default StyleSheet.create({
  container: {
    ...tailwind('flex-1 p-12 justify-between items-stretch'),
  },
});
```

As you can see, I still use the Tailwind utility classes, but I wrapped it in a container so I can reuse it in other components as well! The beauty of both words! 😁

That's it for today friends! I will keep you posted on things I learn along the way of building [my new app](https://blog.andreizgirvaci.com/starting-my-new-startup). Until then, have an amazing rest of your day! See you tomorrow! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*