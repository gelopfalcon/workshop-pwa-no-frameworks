# workshop-pwa-no-frameworks -> Step 1

## Create the web app manifest

So your mission, should you choose to accept it, involves the creation of a new file: `src/manifest.json`. You just need to follow [this reference](https://developers.google.com/web/fundamentals/web-app-manifest/). You can start by copying and pasting the complete version of the manifest. The `build` script will take care of copying it to the `dist` public folder.

Using your manifest your web app should:

* Define both the short (`Rick & Morty`) and the long (`Rick & Morty PWA`) name of the app.
* Only include the mandatory 192x192px and 512x512px icons. They are located in `/assets/img/icons`. Replace their `"src"` accordingly.
* Define `/index.html` as the opened page when the app is first launched.
* Tell the browser you want your app to open in a `standalone` window.
* Not be scoped. Either remove that property or leave it as `/`.
* Use the yellow of our app for the background color: `#fccf6c`. And since the theme color should match the color of the tool bar we will employ `#004d40`.

> Trick: if you use [this Web App Manifest Generator](https://app-manifest.firebaseapp.com/) it will generate all icon sizes for you.

## Add meta and link tags

Open `src/index.html`

Below the last meta tag add these ones:

```html
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<meta name="apple-mobile-web-app-title" content="Rick & Morty PWA" />
<meta name="description" content="PWA with Workbox" />
<meta name="theme-color" content="#004d40" />
```

Below the last link tag ad these ones:

```html
<link rel="manifest" href="/manifest.json" />
<link rel="apple-touch-icon" href="/assets/img/icons/rick-morty-pwa-icon-512x512.png" />
```

And it would also be very good to add this after your scripts:

```html
<noscript>Please enable JavaScript to continue using this application.</noscript>
```

## Verify changes with Lighthouse

```bash
npm run build
npm run lighthouse
```

We can declare the PWA Optimized section resolved since the HTTPS flag does not represent a problem. In fact notice that in the Installable section we have been always getting the green color on "Uses HTTPS" since `localhost` is allowed as secure.

However, we still have 3 bugs to solve:

* Current page does not respond with a 200 when offline
* start_url does not respond with a 200 when offline
* Does not register a service worker that controls page and start_url

But don't worry. Everything will get better when we implement our service worker.

Click [here](https://github.com/gelopfalcon/workshop-pwa-no-frameworks/tree/step-02-app-shell) to navigate the instructions of the next step.

## If you didn't make it

```bash
git checkout step-01-web-app-manifest
git checkout -b step-01-web-app-manifest-mine
```
