# Requirements



## Core
- cycle infinitely
- animate between images
# Architecture
- ViewModel, model
  - tell image component to show which image
- Image
  - display curr image
- prev/next
  - tell viewModel to change curr image
- progress dot
  - choose which image to show
# Data model
> only view model can store state and data
## conf
- list of images(url, alt)
- transition duration
- height width of image

## state
- index of image
- changed by button

# API 
```
<ImageCarousel
  images={[
    { src: 'https://example.com/images/foo.jpg', alt: 'A foo' },
    { src: 'https://example.com/images/bar.jpg', alt: 'A bar' },
    /* More images if desired. */
  ]}
  transitionDuration={300}
  height={500}
  width={800}
/>
```

## Advanced Options
- autoplay
  - have a timer to keep changing image
  - timer need to be restored or canceled if user changed image
- delay between transitions(used in autoplay)
- Event listeners
  - onPageSelect
  - onLoad
  - onNextClick/onPrevClick
- Theming
- Loop
## Internal API
- prevImage - prev btn/ keyboard/
- nextImage - next btn/ keyboard/ timer
- showImage - dot

# Optimization

```
.carousel-images {
  display: flex;
  height: 400px;
  width: 600px;
  overflow: hidden;
}

.carousel-image {
  height: 400px;
  width: 600px;
}
```

滚动
```
document.querySelector('.carousel-images').scrollTo({
  left: selectedIndex * 600,
  behavior: 'smooth',
});
```

## image display
- object-fit(preferred)
- contain
    - scales the image as large as possible. if container > image, it will be tilled -->backgroud-repeat
- cover
    - scales the image as small as possible. if image > container, it will be cropped vertically or horizontally.

## vertically center btn
```
.carousel-image-container {
  height: 400px;
  width: 600px;
  position: relative; /* So that position: absolute will be relative to this element. */
}

.carousel-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%); /* Shifts the button up by half its height. */
}

.carousel-button-prev {
  left: 30px;
}

.carousel-button-next {
  right: 30px;
}
```

## User experience
- CSS scroll snapping
- btn be big enough
- Reposition Prev/Next buttons
    - closer for more convenient

## Performance
- Defer loading of images that aren't on-screen
<img loading="lazy">
- Preloading of images
- Device-specific images
- Virtualized lists

## Accessibility
- Mobile-friendliness
    - alt, aria-label
    - bigger btn
    - keyboard support