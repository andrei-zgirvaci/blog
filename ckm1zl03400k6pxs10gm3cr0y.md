## Creating a slick, yet accessible email signature! 🖋

A few months ago, I decided to replace my old email signature with a new better looking one.

For reference, this is the old email-signature:

![Screenshot 2021-03-09 at 7.27.17 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615289497387/VP3HN2uAT.png)

For some reason, I thought my e-signature didn't look that bad, let's just say I needed a good wake-up call! 🤦‍♂️

I went on to dribbble.com to find some inspirations. I found many nice looking ones with shadows, gradients, etc... But, unfortunately, it's not that easy to create a good-looking e-signature and at the same time make it accessible across all the email clients (or at least most of them...)

In the end, these are the designs I got inspired from:

1. For this one, I really liked the overall look of it!
![Screenshot 2021-03-09 at 7.34.31 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615289696445/jOkRjz03g.png)
[Link](https://dribbble.com/shots/9239162-Email-Signatures)

2. And for this, I liked the CTA button.
![Screenshot 2021-03-09 at 7.34.19 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615289700891/qkNqVkDj3.png)
[Link](https://dribbble.com/shots/5939866-Bondspark-Email-Signature)

At the start, I tried to use the [MJML](https://mjml.io/) framework to build my signature, but it turned out to be more difficult as its purpose is to build responsive emails, not email signatures.

So, after a day of wasting my time with MJML, I decided to go my own way and build it from scratch...

**DISCLAIMER**: *Prepare for some old school sh&ast;t and forget about Flex layout! Heck, you can't even use shadows or custom fonts! You are gonna build an email signature using tables and inline-styles! YAY! 🎉*

Here are some resources to get you started on the right foot!
- https://css-tricks.com/using-css-in-html-emails-the-real-story/
- https://medium.com/@robertcooper_rc/creating-slick-email-signatures-using-html-css-9e932758a41e

If you read those articles and you still want to create your email-signature, then it means you really want it, so let's get to work! 🔨

### Here are some advices from me: 
- If you want to make your text italic, bold, add quotes, etc... It's better to use HTML tags specified for that instead of doing it through CSS! - htmlreference.io

- Make sure to add this attributes to your table:
```html
<table cellpadding="0" cellspacing="0" role="presentation">
```

- If you want to use icons, for example, social-media brands, you have to use .PNG or .JPEG images. SVG is not yet supported in most of the email clients! I used imgur.com to host my images.

- You can create classes and style those, but your end code should be transformed into inline-style css. This is a great tool that will help you do just that! - templates.mailchimp.com/resources/inline-css

- If you are not sure if a CSS property will be supported or not, you can use these websites - [1](https://www.campaignmonitor.com/css/), [2](https://templates.mailchimp.com/resources/email-client-css-support/)

- I like to make everything I build accessible, so make sure to check your code to be accessible too! - [1](https://validator.w3.org/#validate_by_upload), [2](https://achecker.ca/checker/index.php)

- Make sure to minify your code when you are done - willpeavy.com/tools/minifier

After you are done, you have to import your signature into your email client. Every email client handles this differently. I use the apple mail and I used [this tutorial](http://matt.coneybeare.me/how-to-make-an-html-signature-in-apple-mail-for-mojave-os-x-10-dot-14/). Make sure you import just the BODY tag and minify your code before pasting it into the file!

### Here is my new signature 😊

![Screenshot 2021-03-09 at 7.24.41 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615291754958/jaoSqETPf.png)

Hope this was useful to you guys in case you want to build your email-signature! See you tomorrow 😊

---

BTW, yesterday, I have published a new episode of [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it.

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*
