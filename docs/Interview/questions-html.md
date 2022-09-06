# Interview - HTML

## Concepts

### SEO

### Semantic

[What Is Semantic HTML and Why You Should Use It](https://www.lifewire.com/why-use-semantic-html-3468271)

### Accessibility

- using correct elements like buttons instead of div
- good semantic (a, button, p)
- keyboard accessibility (tabindex="0")
- images alternative texts or (aria-labelledby="dino-label")

[Learn JavaScript Accessibility Features for Making Your JavaScript Web Applications More Accessible with Marcy Sutton.](https://frontendmasters.com/courses/javascript-accessibility/)

## Questions

### How browser parse HTML?

On the page load, HTML and CSS are being parsed simultaneously. HTML creates the DOM (Document Object Model) and CSS creates the CSSOM (CSS Object Model).

### What is DOCTYPE?

It is used to tell user agents what version of the HTML specifications your document respects. For webpages, the DOCTYPE declaration is required.

The DOCTYPE declaration for the HTML5 standards is:

```html
<!DOCTYPE html>
```

### How to serve multilanguages content?

The returned HTML document should also declare the lang attribute in the `<html>` tag, such as:

```html
<html lang="en">...</html>
```

You must also make use of the hreflang attribute in the `<head>` for letting a search engine know that the same content is available in different languages. Eg.

```html
<link rel="alternate" hreflang="de" href="http://de.example.com/page.html" />
```

### What is `data-` attributes?

Very popular method for old javascript code before react for example to store additionall data within the DOM.

Now they are using mostly for testing freamworks like Selenium for easy find elements of the page.

### Describe HTML5 APIs

- Battery API
- DOM
- Fetch API
- File System API
- Geolocation API
- History API
- Pointer Events
- Service Workers API
- Storage
- Vibration API
- Web Storage API
- Web Workers API
- WebGL
- Websockets API

### Describe the difference between `cookie` `sessionStorage` `localStorage`

All the above-mentioned technologies are key-value storage mechanisms on the client side. They are only able to store values as strings.

|  | `cookie` | `localStorage` | `sessionStorage` |
| --- | --- | --- | --- |
| Initiator | Client or server. Server can use `Set-Cookie` header | Client | Client |
| Expiry | Manually set | Forever | On tab close |
| Persistent across browser sessions | Depends on whether expiration is set | Yes | No |
| Sent to server with every HTTP request | Cookies are automatically being sent via `Cookie` header | No | No |
| Capacity (per domain) | 4kb | 5MB | 5MB |
| Accessibility | Any window | Any window | Same tab |

### Describe the difference between `<script>`, `<script async>` and `<script defer>`

`<script>` browser is waiting for fetch all data from url and HTML parsing is continue after that

`<script async>` used for analytics, do not block the page, feched during HTML parsing, executed if available

`<script defer>` like before but executed after page has finished parsing. A deferred script must not contain document.write.

The `async` and `defer` attributes are ignored for inline code and without src address.

### Technics for improve visible rendering - progressive rendering?

- lazy loading of images
- prioritizing visible content
- async html fragments

### What is the `srcset` atrribute for image tag?

Serve higher quality images to devices with for example retina display.

```html
<img srcset="small.jpg 500w, medium.jpg 1000w, large.jpg 2000w" src="..." alt="">
```

For a device width of 320px, the following calculations are made:

- 500 / 320 = 1.5625
- 1000 / 320 = 3.125
- 2000 / 320 = 6.25

If the resolution is retina (2x), the browser will use the closest resolution above the minimum. Meaning it will not choose the 500w (1.5625) because it is greater than 1 and the image might look bad.

### What is template HTML language?

Pug (formerly Jade), ERB, Slim, Handlebars, Jinja, Liquid, and EJS just to name a few. In my opinion, they are more or less the same and provide similar functionality of escaping content and helpful filters for manipulating the data to be displayed.

## Sources

[What Is Semantic HTML and Why You Should Use It](https://www.lifewire.com/why-use-semantic-html-3468271)
