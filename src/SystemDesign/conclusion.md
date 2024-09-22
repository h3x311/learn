# Requirements
## Devices
- Desktop
- Tablet
- mobile

## QA
- What are the most critical aspects of the component?
  - core features
- What are the non-functional requirements?
  - 
- what kind of xx should be supported?
  - format(text, image media)
- what devices will this component be used on?
  - Primarily desktop but it should also be usable on tablet and mobile.
- Do we need to support fuzzy search?

# Architecture
- Server: Provide http APIs to fetch data and to create xx
- Controller: control the flow of data within the application and makes network requests to the server
- client store: store data needed across the whole application. In the context of xx, most of the data in the store will be server-originated data needed by the xx UI
- UI: Contains a list of xx and Ui for xx
  - classification
- Rendering approach
  - Server side rendering
    - Friendly for SEO
  - Client side rendering
    - interactive content
  - Hybrid
- Single-page application (SPA) or Multi-page application (MPA)?
  - 
# Data model
| Entity | Source | Belongs to | Fields                                      |
|--------|--------|------------|---------------------------------------------|
| Feed   | Server | Feed UI    | posts,pagination  |
|   Posts     |    Server    |  Feed Posts   |  id, created_time, content, author, reactions, image_url    |
|   User     |    Server    |  ClientStore   |    id, name, avatar  |

# API 
- Http method
- Path
- description
- parameters

# Optimization
List virtualization
    列表虚拟化
    Accessible forms
    无障碍表格
    Normalized store
    正规化门店

## Performance
### Optimized images
- Image carousel
- Image preloading/lazy loading
- use webp
### Lazy loading and Code splitting JavaScript for faster performance
- Split on the page level
- Lazy loading resources within a page
### Performance monitor
- Light house 
## User Experience
## Accessibility
### Keyboard shortcuts
## SEO
- readable URL
## Internationalization
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

## 3 tier
- load UI skeletons for initial loading 
- fully render all above-the-fold content
-  including logging code and subscriptions for live-updating data.

## Error States
Clearly display error states if any network requests have failed, or when there's no network connectivity.

## dynamic rendering
- render different version for users and crawlers(Static html)
