# React Once

> ⚠️ This is pre-release stuff, and while it may be a good starting off point, it doesn't have the easy upgradability that I might like to add if people are interested. There may be bloat left over from years of updating this codebase (going back 6 years), but that too can be fixed if there's interest.

### Learn once, Write once, React Once, Use Everywhere

##### What it is

React is the declarative UI framework that became popular as a JS web front-end framework, before becoming amazing by translating JS code into native iOS and then Android apps. What now? Well, `react-native-web` bridges some gaps and lets you write web React like it was iOS/Android React. Recently, the day came that iPad apps could then run on macOS, and now I've been writing multi-platform apps with the same source code and amazing performance. This tries to share that experience as a starter kit. This code aims to run React everywhere, so uses Next v9 for server-side rendering which covers a lot of SEO bases.

##### TLDR

✅ Web support and full Next/SSR benefits
✅ iOS support
✅ macOS support
✅ Very streamlined Redux
✅ Flow type checking
✅ Multi-language support
✅ Example code including auth
✅ Custom icon examples
⚠️ I have not tested it on android yet, fyi

##### Stop calling it React Native

I've been frustrated by peers and employers who see React and React Native as overly separate? It's like when people confuse Javascript for Java, but in reverse. We added on "Native" to the name "React" and it's like I have to write separate resumes for each. Whatever we call it, I hope we can enjoy writing universal, native code bases in a declarative way. I know I do.

## Installation

This repo helps in initializing a template. It's a cli tool in the vein of `create-react-app`. **Important: after running the create command below, create a `.env` file containing `API_HOST=http://localhost:3001`. This will let you run with the mock API.**

```
npx create-react-once-app my-app
cd my-app
npm run dev
```

And as standard on iOS:

```
cd ios
pod install
cd ..
```

And then use `npm run ios` or open it in XCode to run. **To run on macOS you must also do it in XCode** as I haven't added a script for that yet. See below for notes on M1 (which I use with success).

### Routing

Because we use `react-navigation` for "Native" (oops I called it native) and `next` for web/SSR, we use `expo-next-react-navigation` for most links. But that doesn't mean we still don't have to maintain a `src/pages` folder for Next's routing and `react-navigation` in `App.js`. With smart coding, this is not too hard. The docs of `expo-next-react-navigation` should show how similar it is to `react-navigation`, but it means understanding Next's file/folder based routing.

### Redux / State management

In this app kit, a great deal of Redux boilerplate is taken care of using `ApiClient.js` which adds authentication to requests, and adds a minimal but powerful client for REST requests (promises-based) to each Redux action so they can be written in just a few lines. Look under `src/store` for implementation, and `src/store/modules` for examples of reducers (which if you replicate, add to `reducers.js`).

## Installation on M1 macsOS ~11.2

Development is screaming fast on the M1 Macs. However, there is mixed success getting Cocoapods working with `pod install`. The method I used to get around this is to do pod install like so `cd ios && arch -x86_64 pod install`. This does NOT force you to use Rosetta (at least it doesn't seem to) for XCode and everything else too. It seems to make great use of the M1 and is extremely fast and never turns on the fans. Version 1.11.0 of Cocoapods is planned to fix this issue and perhaps install natively on M1 which will be a slightly smoother install and maybe even somehow faster, if that's possible.
