# Code splitting JavaScript for faster performance
- Split on the page level
- Lazy loading resources within a page

## 3 tier
- load UI skeletons for initial loading 
- fully render all above-the-fold content
-  including logging code and subscriptions for live-updating data.

# Keyboard shortcuts

# Error States


# SEO

- readable URL

# dynamic rendering
- render different version for users and crawlers(Static html)

# Internationalization
Have dedicated pages translated in the supported languages.
Make the language and country selector very prominent (e.g. in the navbar).
For listing details which are contributed by users, add an automatic translation feature so that users visiting country X but don't speak country X's language can understand the listing in their native language.
Set the lang attribute on the html tag (e.g. <html lang="zh-cn">) to tell browsers and search engines the language of the page which helps browsers offer a translation of the page. This is also important for SEO.
Enable locale-specific UI:
    Using the :lang() CSS pseudo-class to change display
    Right-to-left languages
        Using CSS Logical Properties
        HTML's dir attribute
        CSS direction: rtl
Consider differences in the length of text in different languages.
Do not concatenate translated strings.
Do not put text in images.
Be mindful of how colors are perceived in different cultures.

# Performance

## Image

- Image carousel
- Image preloading/lazy loading
- use webp

## Code split

## Performance monitor

- Light house 

