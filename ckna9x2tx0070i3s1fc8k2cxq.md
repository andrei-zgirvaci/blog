## Some progress on the Trustio App 📈

Today I and my team after a long week of debugging and trying different guides from the docs, managed to solve a bug in Amplify where the lamda wasn't executing the GraphQL API call due to unauthorized access! 😓

It turned out, we forgot to give  [IAM access](https://docs.amplify.aws/guides/functions/graphql-from-lambda/q/platform/js#signing-a-request-from-lambda) to our API Link. We thought we did by updating the lambda function resources, but what we also needed to do, is to give access from the API itself by running `amplify update api` and that fixed our problem. 🙌

Also, today I upgraded my app to `react-hook-form` from [v6 to v7](https://react-hook-form.com/migrate-v6-to-v7/). My app got a lot cleaner after refactoring the codebase, which makes me very happy! 😊

The app is almost done and what's left to do is to just hook the front-end with the back-end, hopefully, that is not gonna take too much time...

That's it for today folks! See you next Monday! Love you all! ❤️

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*