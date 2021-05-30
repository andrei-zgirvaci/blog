## My portfolio is live! 🎉

Today I finally bought a domain at  [andreizgirvaci.com](https://andreizgirvaci.com) 🎉

I am not sure if I am the only one, but I feel like I am finally an adult because now I own my own domain and have a personal portfolio on it. 💪

I used [namecheap.com](https://namecheap.com) to buy my domain which came up pretty cheap: ~$9 and I used a coupon that dropped the price even more, to: ~$7. I always like to get things cheaper 🤷‍♂️. P.s here is the coupon if you would like to use it: **COUPONFCNC**

It was super easy to connect my present website which is hosted on [vercel.com](https://vercel.com) to my domain.

Next step was to add some SEO meta tags, here is a list if you would like to use them:
```jsx
<meta name="viewport" content="width=device-width, initial-scale=1" />

<link rel="canonical" href={META.siteUrl}></link>
<link rel="icon" href="/favicon.ico" />
<meta name="theme-color" content="#7f5af0" />

<title>{META.title}</title>
<meta name="description" content={META.description} key="description" />

{/* Twitter */}
<meta
  name="twitter:card"
  content="summary_large_image"
  key="twitter_card"
/>
<meta name="twitter:title" content={META.title} key="twitter_title" />
<meta
  name="twitter:description"
  content={META.description}
  key="twitter_description"
/>
<meta
  name="twitter:image:src"
  content={META.image}
  key="twitter_image"
/>
<meta
  name="twitter:image:alt"
  content={META.imageAlt}
  key="twitter_image_alt"
/>
<meta
  name="twitter:site"
  content={META.twitterHandle}
  key="twitter_site"
/>
<meta
  name="twitter:creator"
  content={META.twitterHandle}
  key="twitter_creator"
/>

{/* Open Graph */}
<meta property="og:type" content="website" key="og_type" />
<meta property="og:title" content={META.title} key="og_title" />
<meta
  property="og:description"
  content={META.description}
  key="og_description"
/>
<meta
  property="og:image"
  content={META.image}
  key="og_image"
/>
<meta
  property="og:image:alt"
  content={META.imageAlt}
  key="og_image_alt"
/>
<meta
  property="og:site_name"
  content="Andrei.Zgirvaci"
  key="og_site_name"
/>
<meta property="og:url" content={META.siteUrl} key="og_url" />
```

You can see that I use `key`, this ensures there will be no duplicates in the `<head>` if similar metas appear later in other pages. I am using [next.js](https://nextjs.org/docs/api-reference/next/head) btw... Also, you might see that I use a const `META` which is basically a JSON file where I store all my meta content.

Also, it's a good idea to verify your domain on [google search](https://support.google.com/webmasters/answer/9008080?hl=en) which will also benefit your SEO!

Another cool thing I managed to do today was to link my current blog to my domain. Now you can find my blog at  [blog.andreizgirvaci.com](https://blog.andreizgirvaci.com) 😊 

And just as a side note, when you move your blog from hashnode to your domain, all the SEO will be transferred which is super cool! This is a tweet where Sandeep Panda (Founder of Hashnode) confirmed my assumption!

%[https://twitter.com/sandeepg33k/status/1365296725053767683]

That's it for today folks! It was quite a busy week for me trying to get this portfolio done. 🏋️‍♀️ Next week I will add my new website to my email signature and also will share it with you so you can see the process of how I built it. 😊 Till next time! 👋

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*