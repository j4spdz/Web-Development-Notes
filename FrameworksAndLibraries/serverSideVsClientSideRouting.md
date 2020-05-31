# [Server-side vs Client-side Routing](https://medium.com/@wilbo/server-side-vs-client-side-routing-71d710e9227f)

## Routing

Routing is the mechanism by which requests are connected to some code. It is essentially the way you navigate through a website or web-application. By clicking on a link, the URL changes which provides the user with some new data or a new webpage.

## Server-side

A server-side request causes the whole page to refresh. This is because a new GET request is sent to the server which responds with a new document, completely discarding the old page altogether.

### Pros

- A server-side route will only request the data that’s needed.
- search engines are optimised for webpages that come from the server.

### Cons

- Every request results in a full-page refresh. That means that unnecessary data is being requested.
- It can take a while for the page to be rendered when document is large or the internet speed is slow.
  
## Client-side

A client-side route happens when the route is handled internally by the JavaScript that is loaded on the page. 

When a user clicks on a link, the URL changes but the request to the server is prevented. The adjustment to the URL will result in a changed state of the application. The changed state will ultimately result in a different view of the webpage. This could be the rendering of a new component, or even a request to a server for some data that the application will turn into some HTML elements.

### Pros

- Because less data is processed, routing between views is generally faster.
- Smooth transitions and animations between views are easier to implement.

### Cons

- Long initial load time as the whole website or web-application needs to be loaded on the first request. In addition, it's possible for to download data for views you won’t even come across.
- It requires more setup work or even a library. Because server-side is the standard, extra code must be written to make client-side routing possible.
- Search engine crawling is less optimised.
