[![GitHub release](https://img.shields.io/github/release/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/releases/latest)
[![GitHub issues](https://img.shields.io/github/issues/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/issues)
[![GitHub last commit](https://img.shields.io/github/last-commit/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/commits/master)
[![Build Status](https://travis-ci.org/scriptex/create-pwa.svg?branch=master)](https://travis-ci.org/scriptex/create-pwa)
[![npm](https://img.shields.io/npm/dt/create-pwa.svg)](https://www.npmjs.com/package/create-pwa)
[![npm](https://img.shields.io/npm/v/create-pwa.svg)](https://www.npmjs.com/package/create-pwa)
[![Analytics](https://ga-beacon.appspot.com/UA-83446952-1/github.com/scriptex/create-pwa/README.md)](https://github.com/scriptex/create-pwa/)

# create-pwa

Easily create a progressive web app

## About

`create-pwa` is a module for quick scaffolding and producing of progressive web applications.

`create-pwa` adds the minimum required boilerplate which your app requires in order to become a PWA.

`create-pwa` can be used with existing applications or can be the first thing one does when starting a new app.

## Dependencies

In order to use this module, you must have NodeJS installed and NPM or Yarn available.

## Install

```sh
# Using NPM:
npm i create-pwa --save-dev

# Using Yarn
yarn add create-pwa --dev
```

## Arguments

1. `icon`: Specifies relative path to the application icon.

This path is relative to the folder you are located in. It is recommended that the icon file should be at least 512 pixels wide and 512 pixels high.

**The `icon` argument is not required.**

2. `launch`: Specifies relative path to the application launch (splash) screen

This path is relative to the folder you are located in. It is recommended that the launch file should be at least 3200 pixels wide and 3200 pixels high and the actual content (for example brand image) should be located in the middle of the image in a square with dimensions up to 500 pixels wide and 500 pixels high.

**The `splash` argument is not required.**

## Usage

First, navigate to your application's folder:
Then run the install command (see above)

```sh
cd your/app/folder

create-pwa --icon="./icon.png" --launch="./launch.png"
```

You can also use `create-pwa` as a package.json script:

```json
{
	"scripts": {
		"pwa": "create-pwa --icon=\"path/to/your/icon.png\" --launch=\"path/to/your/launch.png\""
	}
}
```

The above commands will generate `manifest.json` and `service-worker.js` files, several (8) png icons in the `/icons/` folder in your app's root folder and several (20) launch screen images in the `launch-screen` folder in your app's root folder.

You can edit the contents of the `manifest.json` and `service-worker.js` files.

Their default content is based on industry's best practices and is highly opinionated.

In order to create a customized experience for your users, feel advised to revise and edit the contents of the above files.

When the files(`manifest.json` and `service-worker.js`) are ready for production, you need to let the world know about them:

1.  Add the following to the `head` of your HTML file(s):

```html
<link rel="manifest" href="manifest.json" />
```

You can read more about the Web App Manifest [here](https://developers.google.com/web/fundamentals/web-app-manifest/).

2.  Add the following snippet to your application's JavaScript bundle or place it in a `script` tag just before the closing `</body>` tag in your HTML file(s):

```javascript
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./service-worker.js').then(registration => {
        console.log(`ServiceWorker registration successful with scope: ${registration.scope}`);
    }, error => {
      console.log(`ServiceWorker registration failed: ${error}`);
    });
  });
}
```
The code above checks for service worker support and then registers a service worker located in the `service-worker.js` file in the root of the project.

You can read more about Service Workers [here](https://developers.google.com/web/fundamentals/primers/service-workers/).

3. Add the following to the `head` of your HTML file(s):

```html
<!-- 12.9" iPad Pro Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2048x2732.png" media="(device-width: 2048px) and (device-height: 2732px) and (orientation: portrait)" />
<!-- 12.9" iPad Pro Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2732x2048.png" media="(device-width: 2732px) and (device-height: 2048px) and (orientation: landscape)" />
<!--  11" iPad Pro Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1668x2388.png" media="(device-width: 1668px) and (device-height: 2388px) and (orientation: portrait)" />
<!--  11" iPad Pro Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2388x1668.png" media="(device-width: 2388px) and (device-height: 1668px) and (orientation: landscape)" />
<!-- 10.5" iPad Pro Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1668x2224.png" media="(device-width: 1668px) and (device-height: 2224px) and (orientation: portrait)" />
<!-- 10.5" iPad Pro Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2224x1668.png" media="(device-width: 2224px) and (device-height: 1668px) and (orientation: landscape)" />
<!--  9.7" iPad Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1536x2048.png" media="(device-width: 1536px) and (device-height: 2048px) and (orientation: portrait)" />
<!--  9.7" iPad Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2048x1536.png" media="(device-width: 2048px) and (device-height: 1536px) and (orientation: landscape)" />
<!--7.9" iPad mini 4 Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1536x2048.png" media="(device-width: 1536px) and (device-height: 2048px) and (orientation: portrait)" />
<!--7.9" iPad mini 4 Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2048x1536.png" media="(device-width: 2048px and (device-height: 1536px) and (orientation: landscape)" />
<!--  iPhone XS Max Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1242x2688.png" media="(device-width: 1242px and (device-height: 2688px) and (orientation: portrait)" />
<!--  iPhone XS Max Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2688x1242.png" media="(device-width: 2688px) and (device-height: 142px) and (orientation: landscape)" />
<!--  iPhone XS Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1125x2436.png" media="(device-width: 1125px) and (device-height: 236px) and (orientation: portrait)" />
<!--  iPhone XS Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2436x1125.png" media="(device-width: 2436px) and (device-height: 1125px) and (orientation: landscape)" />
<!--  iPhone XR Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-828x1792.png" media="(device-width: 828px) and (device-height: 192px) and (orientation: portrait)" />
<!--  iPhone XR Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1792x828.png" media="(device-width: 1792px) and (device-height: 28px) and (orientation: landscape)" />
<!--  iPhone X Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1125x2436.png" media="(device-width: 1125px) and (device-height: 236px) and (orientation: portrait)" />
<!--  iPhone X Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2436x1125.png" media="(device-width: 2436px and (device-height: 1125px) and (orientation: landscape)" />
<!--  iPhone 8 Plus Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1242x2208.png" media="(device-width: 1242px and (device-height: 2208px) and (orientation: portrait)" />
<!--  iPhone 8 Plus Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2208x1242.png" media="(device-width: 2208px) and (device-height: 1242px) and (orientation: landscape)" />
<!--  iPhone 8 Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-750x1334.png" media="(device-width: 750px) and (device-height: 134px) and (orientation: portrait)" />
<!--  iPhone 8 Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1334x750.png" media="(device-width: 1334px and (device-height: 750px) and (orientation: landscape)" />
<!--  iPhone 7 Plus Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1242x2208.png" media="(device-width: 1242px and (device-height: 2208px) and (orientation: portrait)" />
<!--  iPhone 7 Plus Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2208x1242.png" media="(device-width: 2208px) and (device-height: 1242px) and (orientation: landscape)" />
<!--  iPhone 7 Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-750x1334.png" media="(device-width: 750px) and (device-height: 134px) and (orientation: portrait)" />
<!--  iPhone 7 Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1334x750.png" media="(device-width: 1334px and (device-height: 750px) and (orientation: landscape)" />
<!--  iPhone 6s Plus Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1242x2208.png" media="(device-width: 1242px and (device-height: 2208px) and (orientation: portrait)" />
<!--  iPhone 6s Plus Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-2208x1242.png" media="(device-width: 2208px) and (device-height: 1242px) and (orientation: landscape)" />
<!--  iPhone 6s Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-750x1334.png" media="(device-width: 750px) and (device-height: 134px) and (orientation: portrait)" />
<!--  iPhone 6s Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1334x750.png" media="(device-width: 1334px) and (device-height: 50px) and (orientation: landscape)" />
<!--  iPhone SE Portrait -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-640x1136.png" media="(device-width: 640px) and (device-height: 136px) and (orientation: portrait)" />
<!--  iPhone SE Landscape -->
<link rel="apple-touch-startup-image" href="./launch-screens/launch-screen-1136x640.png" media="(device-width: 1136px) and (device-height: 640px) and (orientation: landscape)" />
```

4. (Optional) Add the following attribute to your `html` tag: `manifest="<YOUR_APP_NAME>.appcache"`. It should look something like this:

```html
<html lang="en" manifest="create-pwa.appcache">
```

This will enable application cache and will cache all files listed in the `.appcache` file.
Application cache is currently deprecated in most evergreen browsers and will probably be removed soon.
This, however, does not mean that you can not use it in older browsers (for example IE 11).

You can read more about Application Cache [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Using_the_application_cache)

## More info

There is a lot information about Progressive Web Applications on the Internet.
In order to comply with browser's requirements and pass the audits you need to check out and fulfill the [PWA Checklist](https://developers.google.com/web/progressive-web-apps/checklist).

The entries listed in **Baseline Progressive Web App Checklist** are mandatory and without them your web app will not qualify as a PWA.

If you wish to test your web app's compliance, you can use the Chrome's built-in Lighthouse tool (found under the _Audits_ tab in the Developer tools).

## LICENSE

MIT
