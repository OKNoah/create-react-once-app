# React Once

> ⚠️ This is pre-release stuff, and while it may be a good starting off point, it doesn't have the easy upgradability that I might like to add if people are interested. There may be bloat left over from years of updating this codebase (going back 6 years), but that too can be fixed if there's interest.

### Learn once, Write once, Use Everywhere, React Once

##### What it is

React Once is an open example of universal, "write once, run everywhere" using React (Native) syntax and libraries. It runs native on all platforms it currently supports, and showcases many packages working--ones useful in starting a project too.

##### TLDR

🧰 Web support and full Next/SSR benefits

📱 iOS support

🖥 macOS support

🏄‍♀️ Very streamlined Redux

🔍 Flow type checking

🌐 Multi-language support

🔏 Example code including auth

📸 Custom icon examples

⚠️ I have not tested it on android yet, fyi

#### Purpose 

I think in the long run, naming "React Native" what it's called was a mistake. It's made it seem too separate from React in my experience with other devs and companies. The mantra of "learn once, write anywhere" was very important as it set realistic goals for the time. It's let us use this declarative UI framework on web and mobile for the past 7 years, whereas if they'd tried to make it work universally since day one it'd either have the same downsides as other "write once" libraries that use web views, or taken ages to be released.

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

## Source code

The source code is located here (https://gitlab.com/NoahGray/react-once-template/-/tree/main/template), and all tickets can be found there, or added there. 

### Routing

Because we use `react-navigation` for "Native" (oops I called it native) and `next` for web/SSR, we use `expo-next-react-navigation` for most links. But that doesn't mean we still don't have to maintain a `src/pages` folder for Next's routing and `react-navigation` in `App.js`. With smart coding, this is not too hard. The docs of `expo-next-react-navigation` should show how similar it is to `react-navigation`, but it means understanding Next's file/folder based routing.

### Redux / State management

In this app kit, a great deal of Redux boilerplate is taken care of using `ApiClient.js` which adds authentication to requests, and adds a minimal but powerful client for REST requests (promises-based) to each Redux action so they can be written in just a few lines. Look under `src/store` for implementation, and `src/store/modules` for examples of reducers (which if you replicate, add to `reducers.js`).

## Installation on M1 macsOS ~11.2

Development is screaming fast on the M1 Macs. However, there is mixed success getting Cocoapods working with `pod install`. The method I used to get around this is to do pod install like so `cd ios && arch -x86_64 pod install`. This does NOT force you to use Rosetta (at least it doesn't seem to) for XCode and everything else too. It seems to make great use of the M1 and is extremely fast and never turns on the fans. Version 1.11.0 of Cocoapods is planned to fix this issue and perhaps install natively on M1 which will be a slightly smoother install and maybe even somehow faster, if that's possible.
