## My AWS Amplify experience so far! 😊

After posting a not so positive article about  [my experience with aws-amplify](https://blog.andreizgirvaci.com/avoid-these-aws-amplify-mistakes). The [AWS Amplify](https://twitter.com/edelman215)  team has reached me the same day, fixed the bug and released a new version of aws-amplify-react-native: **4.3.2** that contains the bug fix ([64357b1](https://github.com/aws-amplify/amplify-js/commit/64357b109dbf098c5b4050b698d43ab32f51e0d4)). Supper responsive, kuddos to them! 🔥

Today, I spent most of my day trying to learn about GraphQL and how to create a schema within the aws-amplify api. Luckly,  [the documentation](https://docs.amplify.aws/cli/graphql-transformer/overview)  was pretty solid covering everything I needed to understand how to create a schema from scratch and even build more complex ones that require `@connections` and custom `@keys`. However it was a little bit hard to find as I was not expecting this useful information to be under the **CLI** section... 🤔 Also, I learned how to create a post-confirm lambda function that will add a user to the DynamoDB every time a new user signs up.  [This guide](https://docs.amplify.aws/guides/functions/cognito-trigger-lambda-dynamodb/q/platform/js)  explains the process really well!

Also, I just discovered today that there is a way to test aws-amplify changes without having to push them every time using the  [mock](https://docs.amplify.aws/cli/usage/mock)  command. I haven't had time to try it yet, but I am curious to see how it works tomorrow.

Over than that, I am still a little bit confused on what is the difference between the `aws.DynamoDB()` and `aws.DynamoDB.DocumentClient()` as in  [one guide](https://docs.amplify.aws/guides/functions/cognito-trigger-lambda-dynamodb/q/platform/js#create-the-lambda-function)  it says to use the `aws.DynamoDB()` and in  [another guide](https://docs.amplify.aws/guides/functions/dynamodb-from-js-lambda/q/platform/js)  it says to use `aws.DynamoDB.DocumentClient()`. I do prefer the simplicity of the `aws.DynamoDB.DocumentClient()`, but not sure if there are some pitfalls to it. One thing I am worried about, is the the missing `__typename` parameter when putting items into tables using `aws.DynamoDB.DocumentClient()` compared to `aws.DynamoDB()`. If anyone knows the answer, please let me know in the comments. Would really appreciate it! 🙏


That's it for today folks! See you tomorrow! 😊

---

p.s 🤫 I recently started a podcast called [The Anxious Developer](https://apple.co/39yOnvz) where I share my knowledge on how to reduce your stress, become more present and productive as a Developer. I would love to hear your thoughts on it! 😊

*Remember, you are worthy, you are loved and you matter! Have a great day! ❤️*