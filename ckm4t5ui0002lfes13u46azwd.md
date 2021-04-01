## Avoid these AWS Amplify mistakes! ✋

Today, I tried for the first time to use AWS Amplify on my new project [trustio.co](https://blog.andreizgirvaci.com/starting-my-new-startup). I am impressed by how many things you can do compared to Firebase, but at the same time I am also a little bit frustrated as the documentation is not that great.

For example, one use case where I tried to handle  [SignIn](https://docs.amplify.aws/lib/auth/emailpassword/q/platform/js#sign-in)  errors which in my opinion is a pretty basic thing to do. Instead of finding answers in their documentation, I had to find them on  [StackOverflow](https://stackoverflow.com/a/65652469).

For example, if I had to solve this problem with Google Firebase, I would just found it explained in their  [docs](https://firebase.google.com/docs/reference/js/firebase.auth.Auth#signinwithemailandpassword), shortly and clearly:

![Screenshot 2021-03-11 at 6.56.11 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615460207092/2ZevjhrMZB.png)

Eventually, I gave up and decided to use their  [UI Components](https://docs.amplify.aws/ui/auth/authenticator/q/framework/react-native)  as it could save me a lot of time! But, it turned out that it has its own pitfalls...

After linking their component with my app pretty fast, I spent a few more hours figuring out why `withAuthenticator` wouldn't accept my `theme` param.

### Update:  [AWS Amplify](https://twitter.com/edelman215)  team has reached me the same day this article was posted, fixed the bug and released a new version of aws-amplify-react-native: 4.3.2 that contains the bug fix ([64357b1](https://github.com/aws-amplify/amplify-js/commit/64357b109dbf098c5b4050b698d43ab32f51e0d4)). Supper responsive! Kuddos to them! 🔥

In their documentation is shown clearly that I can pass the `theme` param in the second param of the `withAuthenticator` component which should be defined in an object:
![Screenshot 2021-03-11 at 7.00.35 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1615460442882/d4UckSau8-.png)

It turns out it's not how it actually works in their codebase!

**Disclaimer:** *Prepare for some dirty work...* 🧐

Let's look at the actual  [component](https://github.com/aws-amplify/amplify-js/blob/main/packages/aws-amplify-react-native/src/Auth/index.tsx) :

```jsx
/* aws-amplify-react-native/src/Auth/index.tsx */

export function withAuthenticator<Props extends object>(
	Comp: React.ComponentType<Props>,
	includeGreetings = false,
	authenticatorComponents = [],
	federated = null,
	theme: AmplifyThemeType = null,
	signUpConfig: ISignUpConfig = {}
) {

/* ... */

if (typeof includeGreetings === 'object' && includeGreetings !== null) {
  this.authConfig = Object.assign(this.authConfig, includeGreetings);
} else {
  this.authConfig = {
    includeGreetings,
    authenticatorComponents,
    signUpConfig,
  };

/* ... */
```

Okay, so, we can clearly see that our `withAuthenticator` component accepts multiple parameters, one of which is `theme` param. Also, you can see the if statement which basically says that in case the second param - `includeGreetings` in `withAuthenticator` is specified as an object, we are gonna treat it as a param with multiple options inside. If not, then we are just gonna assume that the user wants to specify params by comma instead. So far, so good!

&ast; *However, I am not that happy with this implementation as it's quite inconsistent. It would be better if the second parameter was just an object to keep things consistent and not confuse people. Moreover, this is not documented anywhere, so I had to discover this by myself which is not a good sign...*

Okay, let's move on...

If we scroll down, we can see that eventually, `withAuthenticator` is just a wrapper around `Authenticator` component. But...!

```jsx
/* ... */

return (
  <Authenticator
    {...this.props}
    hideDefault={ this.authConfig.authenticatorComponents && this.authConfig.authenticatorComponents.length > 0 }
    signUpConfig={this.authConfig.signUpConfig}
    onStateChange={this.handleAuthStateChange}
    children={this.authConfig.authenticatorComponents}
    usernameAttributes={this.authConfig.usernameAttributes}
    theme={theme}
  />
);

/* ... */
```

you can see that the theme prop in `Authenticator` is taken from our `withAuthenticator` props directly! Not from `this.authConfig` object! This creates problems as you might think that you can specify the `theme` prop in an object and it will be used by the `Authenticator` component as shown in the official  [AWS Documentation](https://docs.amplify.aws/ui/auth/authenticator/q/framework/react-native#using-withauthenticator-hoc) , but in reality, it's not how it works...

So, how do you fix this?

```jsx
export default withAuthenticator(App, {
    includeGreetings: true,
    usernameAttributes: 'email',
    signUpConfig: AmplifySignUpConfig,
  },
  undefined,
  undefined,
  AmplifyTheme
});
```

Not the best solution, but indeed it works as `Authenticator` component would only take the `theme` prop from the 4th param of `withAuthenticator` and not from the 2nd param. 🤷‍♂️

At this point, you might ask, why don't you just use the `Authenticator` component and be done already... Well, I don't want to show the SignOut button after the user logged in the app, but in order to do that, I would have to [specify manually](https://docs.amplify.aws/ui/auth/authenticator/q/framework/react-native#using-the-authenticator-component) which components should `Authenticator` have and which not. Which in turn, adds more code and feels less intuitive. Where in the `withAuthenticator` example, I can just specify a prop like this: `includeGreetings: false` and it makes it really easy to switch things around in development.

As one of the [podcasters](https://twitter.com/umputun) I follow said:
> If you want something done, roll up your sleeves and get to work!

So I might just go on the official repo and open a pull request or just an issue if I am lazy 😁

This is just the first day me working with AWS Amplify, so maybe things will get easier from there or maybe not... 😳 But I do believe AWS Amplify is a better option than firebase, so, let's see...

If you believe I made a mistake and it's not AWS's fault, please correct me in the comments! Would really appreciate it!

That's it for today friends! I will keep you posted on things I learn along the way of building the trustio.co app. Until then, have an amazing rest of your day! See you tomorrow! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

<iframe src="https://embed.podcasts.apple.com/us/podcast/the-anxious-developer/id1538448864?itsct=podcast_box&amp;itscg=30200&amp;theme=light" height="450px" frameborder="0" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation-by-user-activation" allow="autoplay *; encrypted-media *;" style="width: 100%; overflow: hidden; border-radius: 10px; background: transparent;"></iframe>

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*