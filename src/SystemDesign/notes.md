# System_Design_GFE

## Requirements Exploration
- Core features
- What kind of results should be supported?
    - images
    - text
    - media(images with text)
- What devices?

## Architecture

### UI
handle user input and pass to controller

### Result UI
- present results to user
- handle user input

### Cache
- first check cache
- then check database
- then fetch from server

### Controller
- Brain of component
- pass userinput and result between components

### Data Model
- ensure the main key that needs to be stored

#### Normalized Store



### API
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

#### pagination

- offset
  - direct to jump specific page
  - not suitable with frequently updated data
  - performance become worse when the data is large
- cursor
  - size && cursor
  - better performance for large data
  - not influenced by new posts 
  
### Rendering approach
- ssr
- csr
## Optimizations
### General
- code splitting JavaScript for faster performance
  - Split on the page level: Each page will only load the JavaScript and CSS needed on that page
  - Lazy loading resources within a page: Load non-critical resources only when needed or after the initial render, such as code that's only needed lower down on the page, or code that's used only when interacted with (e.g. modals, dialogs).


### Network
#### Failed request
Server requests can sometimes fail, possibly due to the user's flaky internet connection. The component can automatically retry firing the query. In case the server is indeed offline and we are concerned about overloading the server, we could use an exponential backoff strategy.
#### Offline usage
network only”、“network and cache”、“cache only
- read from cache
- Not fire any requests so as not to waste CPU cycles.
- Indicate that there's no network connection somewhere in the component.
### Cache
#### Cache structure

- hashmap
  - id 

#### initial result

### Image rendering
- CDN
- webp format
- img with `alt`
- image loading based on device screen size, use `srcset`
- Adaptive image loading based on network speed

### Performance

- loading speed
  - client side caching
- debounce/throttle
  - limit the number of network requests that can be fired
- memory usage
    - Long-lived pages might have autocomplete components which accumulate too many results in the cache and hog memory. Purging the cache and freeing up memory is essential for such pages. The purging can be done when the browser is idle or total memory/number of cache entries exceed a certain threshold.
- Virtualized lists 
  - If the results contains many items (order of hundreds and thousands), rendering that many DOM nodes in the browser would cost lots of memory and slow down the browser. List virtualization is a technique that we can use here to allow the component can retain its performance at scale.
    - The trick here is to only render the nodes which are visible and recycle DOM nodes instead of creating new ones. We can make the results window give the illusion that it contains that many results with fake off-screen elements that add up to the height of the non-visible result elements.
    - Browser painting: Fewer DOM nodes to render and fewer layout computations to be made.
    - Virtual DOM reconciliation (React-specific): Since the post is now a simpler empty version, it's easier for React (the UI library that Facebook is using to render the feed) to diff the virtual DOM vs the real DOM to determine what DOM updates have to be made.
- loading indicator
    - loading shimmer
- Dynamic loading count
  - For the initial load, we do not know the window height so we need to be conservative and overfetch the number of posts needed. But for subsequent fetches, we know the browser window height and can customize the number of posts to fetch based on that.

### user experience
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
- Accessibility screen readers
  - semantic html
  - aria-labels
  - role
  - aria-label
  - aria-labelledby