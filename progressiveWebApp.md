<!-- omit in TOC -->
# Progressive Web App

Enhance user experience and be as close as native apps. It is already setup in create-react-app.

- Lighthouse, a chrome extension, as a metric to measure PWA
- [An overview of the device integration HTML5 APIs](https://whatwebcando.today/)
- [Submitting PWA to 3 app stores](http://debuggerdotbreak.judahgabriel.com/2018/04/13/i-built-a-pwa-and-published-it-in-3-app-stores-heres-what-i-learned/)
- [PWA Android vs iOS](https://medium.com/@firt/progressive-web-apps-on-ios-are-here-d00430dee3a7)
- [Explore some of the top PWAs from around the world:](https://appsco.pe/)
- [Progressive Web App Checklist](https://web.dev/pwa-checklist/)
- [A list of community-built, third-party tools that can be used to improve page performance](https://progressivetooling.com/)

<!-- omit in TOC -->
## Contents

- [HTTPS](#https)
- [App Manifest](#app-manifest)
  - [Viewport Meta Tag](#viewport-meta-tag)
  - [manifest.json](#manifestjson)
- [Service Worker](#service-worker)

## HTTPS

Anytime you have communication with the server, use HTTPS for security reasons.

Easiest way to get HTTPS is by [Let's Encrypt](https://letsencrypt.org/), a free Certificate Authority. Alternatively, look at [Cloudfare](https://www.cloudflare.com/)

## App Manifest

### Viewport Meta Tag

Without a viewport meta tag, mobile devices render pages at typical desktop screen widths and then scale the pages down, making them difficult to read.

Setting the viewport meta tag lets you control the width and scaling of the viewport so that it's sized correctly on all devices.

```html
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

### manifest.json

Define how the app is going to launch and look

```javascript
{
  "short_name": "React App",
  "name": "Create React App Sample",
  "icons": [
    {
      "src": "favicon.ico",
      "sizes": "64x64 32x32 24x24 16x16",
      "type": "image/x-icon"
    }
  ],
  "start_url": "./index.html",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

[Generating favicon via RealFaviconGenerator](https://realfavicongenerator.net/)

## Service Worker

- A script that the browser run in the background, usually for scripts that do not need any user interaction
- Offline experience
- Background sync
- [Push notifications](https://auth0.com/blog/introduction-to-progressive-web-apps-push-notifications-part-3/)

[isServiceWorkerReady?](https://jakearchibald.github.io/isserviceworkerready/)
