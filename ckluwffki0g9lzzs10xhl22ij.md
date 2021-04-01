## Adding animations to my portfolio using headlessui ✍️

Today, I worked on adding transitions for my portfolio using [headlessui](https://github.com/tailwindlabs/headlessui/blob/develop/packages/%40headlessui-react/README.md#transition).


It wasn't easy figuring out as I had some problems trying to animate absolute elements, but in the end it worked out pretty well... Until I checked my published website.

It turns out, the onPageLoad transitions don't work properly with Next.js. It does work in development mode however...

Currently there is an open [issue](https://github.com/tailwindlabs/headlessui/issues/160) on github where this problem is discussed. Hopefully this gets fixed soon. But, most probably I will have to move to another library, perhaps [framer-motion](https://github.com/framer/motion) 🤔

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*