# System_Design_GFE

## Requirements Exploration
### functional requirements(core features)
-  Basic requirements of the product
### non-functional requirements
- What kind of results should be supported?
    - images
    - text
    - media(images with text)
- What devices/platforms (desktop/tablet/mobile) need to be supported?
- Is offline support necessary?
- Who are the main users of the product?
- What are the performance requirements, if any? (Performance requirements typically fall under non-functional requirements.)

## Architecture
### server
- Serves data and Provides HTTP APIs to fetch data
### Controller
- Controls the flow of data within the application and makes network requests to the server.

### Client Store
- Stores data needed across the whole application. 
### UI
handle user input and pass to controller

### Result UI
- present results to user
- handle user input

### Cache
- first check cache
- then check database
- then fetch from server

#### Normalized Store

## Flux

Action -> Dispatcher -> Store -> View

## Rendering approach
- Server-side rendering (SSR)
    - The traditional way of building websites where the server fetches all necessary data, uses them to create the final markup and sends down the HTML needed every time a user visits a page. Most of the rendering work is done on the server.
- Benefits of SSR:
    - Performance is generally better, First Contentful Paint score is high and SSR-ed pages appear faster than CSR.
    - Lower Cumulative Layout Shift score as the final HTML is already present.
    - SSR allows for personalization of pages (user-specific content) as opposed to static site generation. Personalization is an important factor for conversion as e-commerce platforms scale up.
- Downsides of SSR:
    - Page transitions are slower because the entire page has to be constructed on the server for every request.
    - SEO is important for e-commerce websites, hence SSR should be a priority.
- Client-side rendering (CSR)
    - The server sends down initial HTML which contains the JavaScript to bootstrap the application. The client then fetches the necessary data, combines it with templates and creates the final page, all within the browser. CSR is typically used with Single-page Application models and subsequent navigation don't require a full page refresh. Most of the rendering work is done on the client.

## Pagination

### offset
- direct to jump specific page
- not suitable with frequently updated data
- performance become worse when the data is large
### cursor
- size && cursor
- better performance for large data
- not influenced by new posts 

## Data Model
- ensure the main key that needs to be stored
- belong to `client store` or `server`
## API
- !important: Http method, path, parameters
- number of results
- event listeners
    - input, focus, blur, change, select
- Debounce
    - limit the number of times a function is called(300ms)
- API timeout duration
- cache
    - cache duration
- parameter 
    - query
    - limit
## Optimizations - General
### code splitting JavaScript by routes/pages
- Split content into separate sections and prioritize above-the-fold content while lazy loading below-the-fold content.
- Defer loading of non-critical JavaScript (e.g. code needed to show modals, dialogs, etc.).
- Prefetch JavaScript and data needed for the next page upon hover of links/buttons.

## Optimizations - Network
### Failed request
Server requests can sometimes fail, possibly due to the user's flaky internet connection. The component can automatically retry firing the query. In case the server is indeed offline and we are concerned about overloading the server, we could use an exponential backoff strategy.
### Offline usage
network only”、“network and cache”、“cache only
- read from cache
- Not fire any requests so as not to waste CPU cycles.
- Indicate that there's no network connection somewhere in the component.
### Cache
#### Cache structure

- hashmap
  - id 

#### initial result
## Optimizations - SEO

- have proper `<title>` and `<meta>` tags for description, keywords, and open graph tags.
- Generate a sitemap.xml to tell crawlers the available pages of the website.
- Use semantic markup for elements on the page, which also helps accessibility.
- Ensure fast loading times to help the website rank better in Google search.
- Use SSR for better SEO because search engines can index the content without having to wait for the page to be rendered (in the case of CSR).

## Image rendering
- Images should be hosted on a CDN.
- Use the `WebP` image format which is the most efficient image format that currently exists. 
- img with `alt`
- Lazy load below-the-fold images.
    - Use <img loading="lazy"> for non-critical images.
- Load critical images early.
    - Inline the image within the HTML as a data blob so that there's no need to make a separate HTTP request to fetch the image.
    - Using <link rel="preload"> so they download as soon as possible.
- image loading based on device screen size, use `srcset`
- `Adaptive image` loading based on network speed

## Image Background
- [image-background](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size)
- `Contain`：在不裁剪或拉伸图像的情况下，将图像缩放到其容器内尽可能大的尺寸。如果容器大于图像，这将导致图像平铺，除非将背景重复属性设置为不重复。
- `Cover`：缩放图像（同时保持其比例）到填满容器所需的最小尺寸（即：高度和宽度完全覆盖容器），没有空白空间。如果背景的比例与元素不同，则图像会在垂直或水平方向上被裁剪。
- `object-fit`: 
## Performance

- loading speed
    - client side caching
- loading indicator
    - loading shimmer
- Dynamic loading count
    - For the initial load, we do not know the window height so we need to be conservative and overfetch the number of posts needed. But for subsequent fetches, we know the browser window height and can customize the number of posts to fetch based on that.
- Virtualized lists 
    - If the results contains many items (order of hundreds and thousands), rendering that many DOM nodes in the browser would cost lots of memory and slow down the browser. List virtualization is a technique that we can use here to allow the component can retain its performance at scale.
        - The trick here is to only render the nodes which are visible and recycle DOM nodes instead of creating new ones. We can make the results window give the illusion that it contains that many results with fake off-screen elements that add up to the height of the non-visible result elements.
        - Browser painting: Fewer DOM nodes to render and fewer layout computations to be made.
        - Virtual DOM reconciliation (React-specific): Since the post is now a simpler empty version, it's easier for React (the UI library that Facebook is using to render the feed) to diff the virtual DOM vs the real DOM to determine what DOM updates have to be made.
- debounce/throttle
    - limit the number of network requests that can be fired
- memory usage
    - Long-lived pages might have autocomplete components which accumulate too many results in the cache and hog memory. Purging the cache and freeing up memory is essential for such pages. The purging can be done when the browser is idle or total memory/number of cache entries exceed a certain threshold.


## user experience
- autofocus
- Handle different states
    - Loading: Show spinner when there's a background request.
    - Error: Show an error message with a retry request button.
    - No network: Show an error message that there's no network available.

- mobile friendly
    - Each result item should be large enough for user to tap on if used on mobile.
    - Dynamic number of results depending on viewport window size, but this is better implemented in userland instead.
    - Set helpful attributes for mobile: autocapitalize="off", autocomplete="off", autocorrect="off", spellcheck="false" so that the browser suggestions do not interfere with the user's search.
- keyboard friendly
## Accessibility(a11y)
- Use `semantic elements` where possible: headings, buttons, links, inputs instead of styled <div>s.
- use `img` with `alt`
- role
- `aria-label`
- aria-labelledby
- tabindex
- `<input>s` are linked to their error messages via aria-describedby and error messages are announced with aria-live="assertive"
- Use `<input>s` of the correct types and appropriate validation-related attributes like pattern, minlength, maxlength.

## Security
- Use HTTPS so that all communication with the server is encrypted and that other users on the same Wi-FI network cannot intercept and obtain any sensitive details.
- Payment details submission API should not be using HTTP GET because the sensitive details will be included as a query string in the request URL which will get added to the browsing history which is potentially unsafe if the browser is shared by other users. Use HTTP POST or PUT instead.

## Internationalization(i18n)
- Have pages translated in the supported languages.
    - Set the lang attribute on the html tag (e.g. <html lang="zh-cn">) to tell browsers and search engines the language of the page which helps browsers offer a translation of the page.


