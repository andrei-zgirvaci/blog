## Integrating Google Analytics 4 with Next.js 📈

Today, I decided to add Google Analytics to my [portfolio](https://andrei-zgirvaci.hashnode.dev/building-my-freelance-portfolio-in-nextjs) which was built in Next.js

At first, I thought that I could achieve this with [react-ga](https://github.com/react-ga/react-ga), but after trying to add my GA code I realized that it doesn't support Google Analytics 4, only [Universal Analytics](https://support.google.com/analytics/answer/2790010). At this point, I could go and [enable Universal Analytics](https://support.google.com/analytics/answer/10269537), but I am not into legacy stuff, sorry... 🤷‍♂️

Luckily I found a library that does support Google Analytics 4, it's called [ga-4-react](https://github.com/unrealmanu/ga-4-react). *Disclaimer: It doesn't have a lot of starts, but it works!* 🤫

But integrating it with Next.js is different than just plain react, there a few things you must do!

#### 1. Create a util file in the root project:

```js
/* utils/ga.js */

import Router from 'next/router';
import GA4React from 'ga-4-react';

let ga4react;

export async function init(G) {
  if (!GA4React.isInitialized() && G && process.browser) {
    ga4react = new GA4React(G, { debug_mode: !process.env.production });

    try {
      await ga4react.initialize();

      logPageViews();
    } catch (error) {
      console.error(error);
    }
  }
}

function logPageView() {
  ga4react.pageview(window.location.pathname);
}

function logPageViews() {
  logPageView();

  Router.events.on('routeChangeComplete', () => {
    logPageView();
  });
}

export function logEvent(action, label, category) {
  ga4react.event(action, label, category);
}
```

#### 2. Modify the `_app.js` file to initiate the `ga.js` service:

```js
/* ... */

import { useEffect } from 'react';

import { init } from 'utils/ga';

function MyApp({ Component, pageProps }) {
  useEffect(() => {
    init(process.env.NEXT_PUBLIC_G);
  }, []);

  return <Component {...pageProps} />;
}

export default MyApp;
```

#### 3. Add your GA code as an environment variable:
```
# .env.local

NEXT_PUBLIC_G=G-<YOUR CODE>
```

🎉 Voila, now you should be able to see an active device in Google Analytics  DebugView! If you don't, try to disable your AdBlock as it could create problems sometimes...

That's it for today folks, hope this article was helpful to you! Leave a like and comment if it was! See you tomorrow on another blog post! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*