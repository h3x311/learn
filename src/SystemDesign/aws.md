# Requirements

## Core
- browsing products
- add to cart 
- check out successfully

## Pages
- product list page
  - name, image, price
- product detail page
  - name, image(multiple), desc, price
- cart page
- checkout page

## international
- diff area diff age
## non-functional
- load under 2 seconds
- respond quickly
## devices
laptop, tablet, mobile
## security
sign in to purchase
# Architecture
Pages:

    Product List: Displays a list of product items that can be added to the cart.
    Product Details: Displays details of a single product along with additional details.
    Cart: Displays added cart items and allows changing of quantity and deleting added items.
    Checkout: Displays address and payment forms the user has to complete in order to place the order.
## render
SEO - ssr - mpa/spa(yes)



# Data model
- ProductList server products, pagination 
- prodcut server name, desc, unit_price, currency, primary_img, image_url
- cart items, client store, total price, currency
- address, user input, checkout, name, coutry, stree, city
- payment, card_num, card_expiry, cvv

# API 
- get /prodcuts (size, page, country)
  - specific pages
  - not update frequently
    - not stale
  - total results
- get /products/{id}
- post /cart/products
- put /cart/products/{id}
- delete /cart/products/{id}
- 
# Optimization
## performance
- prefetch
- lazy loading, prioritize
- code spliting


## seo
- title meta
- sitemap - crawler

## image
- webp
- cdn
- priority
- lazy load below the fold images
- load critical images early.

## pay
- addresss diff from diff area
    - use stripe
- auto complete payment form
## accessibilty

- use more semantic elements  other than div
- img with alt
- input with label
  - aria-describedby
  - aria-live="assertive
- input with type
  - pattern, minlength, maxlength

## security

- https
  - especially for payment

## user experience
- store content to cookie
- Make promo code fields less prominent so that people without promo codes