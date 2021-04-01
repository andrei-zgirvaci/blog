## Building my freelance portfolio in Next.js

As mentioned in my previous article [4-year startup failed, going freelance](https://andrei-zgirvaci.hashnode.dev/4-year-startup-failed-going-freelance), I want to start my freelance business. For that, I figured I need a nice-looking portfolio so clients can get their wallets ready once they scroll through it. 😅

### Designing

Because I enjoy the design process and I *don't* suck at it too much, I decided to do it myself 😁

For most of the design work, I used to use Adobe XD, but for this project, I wanted to try Figma as it seems like it's becoming very popular among designers. (now I like it more than Adobe XD)

This is what I came up with after 1 week...

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FgllcMcB8ZFtdrTTdR1SriO%2FPortfolio%3Fnode-id%3D1%253A3" allowfullscreen></iframe>

Not too bad, right?

Here are some resources I was inspired from:
github.com, craig-roush-portfolio-template.webflow.io, rans-fancy-website.webflow.io, purrweb.com

### Coding

First, I thought webflow.com will be a perfect fit as the website doesn't look too complicated. But, after spending 4 hours figuring out the best class names for my elements, I figured out that I would be much more productive in my beautiful VS Code workflow. (I was right... 🤫)

But, it wasn't soo easy... Because I am specialized in React Native, I don't build web apps nowadays and the last time I did, I used Bootstrap and jQuery. I completely forgot how to create responsive designs and how to use CSS on the web.

At first, I thought that I could just build it with Create React App, but then I remembered there is something like Next.js and Gatsby that are pretty hyped lately. So, I decided to have a look and see what they are about. I decided to pick Next.js as I don't see Gatsby so much in my Twitter feed lately. (joined the hype train... 😅) 

Also, for styling, I decided to go yet with another Twitter feed pick. (Tailwind) 🤷‍♂️

Jokes aside, Next.js and Tailwind are pretty cool tools that I found could benefit my website a lot (static site generation) and at the same time, I could learn something new...

I spent around 4 days trying to learn Next.js, Tailwind, the latest CSS additions like Grid, and how to make gradient texts like on github.com.

Building the actual website wasn't too hard. Most of the time I spend in Tailwind documentation trying to remember class names.

One thing I spent quite some time on was this part:

![Screenshot 2021-03-01 at 8.29.34 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1614601780201/jislCxqsT.png)

I couldn't figure out how to rotate the text on the right of the image and at the same time keep the wrapper aware of it (because of the `transform` of the text) for responsive purposes later on.

After a few hours of googling and StackOverflow, I managed to find the solution. I needed to add the height of the text element to the width of the parent like so:

```jsx
<div style={{ width: 'calc(<element width> + 1.25rem)' }}>
  ...
  <h6 className="h-5 -mt-2 origin-bottom-left rotate-90 transform-gpu whitespace-nowrap ...">...</h6>
  ...
```

Where **1.25rem** is the height of the text element :)

### Demo

At the time of writing this article, I haven't made my website fully responsive yet. But, you can already see the WIP result here: https://andreizgirvaci.com

Next on the list is to make it responsive for phones and buy a cool domain. At the moment I am still trying to figure out what should I do with my profile picture when viewing the website on the phone. (let me know in the comments if you have any suggestions, it will be much appreciated! 😊)

Also, if you have any other questions on how I implemented some parts of the website, don't be shy to ask.

See you tomorrow on another fresh blog post as I am gonna write quite a lot this year 😅

%[https://andrei-zgirvaci.hashnode.dev/blogging-almost-every-day-in-2021]

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*