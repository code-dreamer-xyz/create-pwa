[![GitHub stars](https://img.shields.io/github/stars/scriptex/create-pwa.svg?style=social&label=Stars)](https://github.com/scriptex/create-pwa)
[![GitHub forks](https://img.shields.io/github/forks/scriptex/create-pwa.svg?style=social&label=Fork)](https://github.com/scriptex/create-pwa/network#fork-destination-box)
[![GitHub release](https://img.shields.io/github/release/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/releases/latest)
[![GitHub issues](https://img.shields.io/github/issues/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/issues)
[![GitHub last commit](https://img.shields.io/github/last-commit/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa/commits/master)
[![npm](https://img.shields.io/npm/dt/create-pwa.svg)](https://www.npmjs.com/package/create-pwa)
[![npm](https://img.shields.io/npm/v/create-pwa.svg)](https://www.npmjs.com/package/create-pwa)
[![license](https://img.shields.io/github/license/scriptex/create-pwa.svg)](https://github.com/scriptex/create-pwa)
[![Analytics](https://ga-beacon.appspot.com/UA-83446952-1/github.com/scriptex/create-pwa/README.md)](https://github.com/scriptex/create-pwa/)
[![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/scriptex/create-pwa/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/scriptex/create-pwa/graphs/commit-activity)

# create-pwa

Easily create a progressive web app

---

🛠 Status: In Development: `create-pwa` is in constant development.

---

## About

`create-pwa` is a module for quick scaffolding and producing of progressive web applications.

`create-pwa` adds the minimum required boilerplate which your app requires in order to become a PWA.

`create-pwa` can be used with existing applications or can be the first thing one does when starting a new app.

## Dependencies

In order to use this module, you must have NodeJS installed and NPM or Yarn available.

## Install

You can either install `create-pwa` globally:

```console
npm i -g create-pwa
```

or use `npx`:

```console
npx create-pwa
```

## Arguments

`icon`: Specifies relative path to the application icon. This path is relative to the folder you are located in currently (`your/app/folder`).

## Usage

First, navigate to your application's folder:
Then run the install command (see above)

```console
cd your/app/folder

npx create-pwa --icon="./icon.png"
```

The above command will generate a `manifest.json`, `service-worker.js` file and several (8) png icons in the `/icons/` folder in your app's root folder.

You can edit the contents of the `manifest.json` and `service-worker.js` files.

Their default content is based on industry's best practices and is highly opinionated.

In order to create a customized experience for your users, feel advised to revise and edit the contents of the above files.

When the files(`manifest.json` and `service-worker.js`) are ready for production, you need to let the world know about them:

1. Add the following to the `head` of your HTML file(s):

```html
<link rel="manifest" href="manifest.json" />
```

You can read more about the Web App Manifest [here](https://developers.google.com/web/fundamentals/web-app-manifest/).

2. Add the following snippet to your application's JavaScript bundle or place it in a `script` tag just before the closing `</body>` tag in your HTML file(s):

```js
if ('serviceWorker' in navigator) {
  window.addEventListener('load', function() {
    navigator.serviceWorker.register('./service-worker.js').then(
      function(registration) {
        // Registration was successful
        console.log(
          'ServiceWorker registration successful with scope: ',
          registration.scope
        );
      },
      function(err) {
        // registration failed :(
        console.log('ServiceWorker registration failed: ', err);
      }
    );
  });
}
```

You can read more about Service Workers [here](https://developers.google.com/web/fundamentals/primers/service-workers/).

## More info

There is a lot information about Progressive Web Applications on the Internet.
In order to comply with browser's requirements and pass the audits you need to check out and fulfill the [PWA Checklist](https://developers.google.com/web/progressive-web-apps/checklist).

The entries listed in **Baseline Progressive Web App Checklist** are mandatory and without them your web app will not qualify as a PWA.

If you wish to test your web app's compliance, you can use the Chrome's built-in Lighthouse tool (found under the _Audits_ tab in the Developer tools).

## LICENSE

MIT
