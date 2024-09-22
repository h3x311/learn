# Requirements
- core
- pagination
- device
- 

## Core

# Architecture

# Data model
Feed Post User NewPost Image

# API 

## composer
- select photo from device
- edit on photos
  - resize/crop/filter/blur
- add caption
- submit 
1. create api for uploading and post creation yes
- simple to implement
- api is more complex
- we need to wait until upload is finished
- 
2. split
- async 
- parallel http requests
- clients 
# Optimization
- infinite
- virtualized lists
- code splitting
- Preserving feed scroll position
- Timestamp rendering

- image carousel
- webp
  - alt img
- Image loading based on device screen properties
- Adaptive image loading based on network speed

## edit
- crop resize
  - canvas
- filter
  - css - filter - blur/contrast/hue/b5

## Accessibility
- alt
- aria-label for prev/next buttons(icon only buttons)

### Keyboard
- for next/prev button
- <div role="region" aria-label="Image Carousel" tabindex="0">


