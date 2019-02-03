# How to install typescript on react-native project ?

## New project 👍

Since babel 7 was realised, it supports typescript integration. You just have to run :

```
react-native init MyAwesomeProject --template typescript
cd MyAwsomeProject
node setup.js
```

That's all 😏

## I'm using babel 6 or less

For typescript support, you need to use `react-native-typescript-transformer`.

Facebook wrote a great article about how to setup your project with it. Just follow this blog article: https://facebook.github.io/react-native/blog/2018/05/07/using-typescript-with-react-native
