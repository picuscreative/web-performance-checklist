[<img width="110" src="https://avatars3.githubusercontent.com/u/38539999?s=200&v=4g" />](https://picuscreative.com)

# web-performance-checklist

PICUS' Web Performance Checklist is a list of steps that aim to improve overall performance and score on tools such as PageInsights, GTMetrix or Lighthouse, independently of the type of the website.

## List of Performance Improving Steps

### 1. Critical Steps

- Enable browser caching. Set different expiration dates depending on the type of assets (for example, logos should be 1 year)
  - Different asset types should have different expiration rules
- Set caching for different types of assets (json includes, for example)
  - Include caching in every type of file possible (by default, many used file types may not be included)
- Add an initial critical CSS specific folder so that there is no page-blocking content
  - If the top of the initial page is rendered separately from the rest of the style files, this can speed up the page load by a lot
- Add defer condition to all JavaScript files (you need to property order these so that there are no dependency errors in between)
  - Don’t let unnecessary script files stop the page from being loaded
- Avoid 404 requests (use fallbacks on development environment)
  - As the topic describes, avoid file not found errors
- Always enable GZIP compression
  - In either Apache or Nginx, enable gzip compression to speed up file loading by up to 90%

### 2. Useful steps

- Don't use `@import` to load fonts
  - Using `@import` can cause additional delays in the page loading from an external source
- Don't use an initial page redirect
  - If a page redirect is needed in a page load, this causes a slight delay in page presentation
- Optimize the order of styles and scripts so that the render can be faster in the entire page as a whole
  - If an asset, be it a stylesheet of a script, is required to render the part of the page being presented, load it in an order that maximizes the rendering speed
- Place the inline CSS inside the document's head tag
  - Useful so that our page doesn’t wait for all the style assets to be loaded
- Use srcsets on the images (whenever possible)
  - Decreases immensely the total amount of data to be downloaded, specially on mobile devices
- Whenever possible (independent files) use async loading of scripts or, at least, defer these loadings
  - Instead of waiting for all scripts to be loaded, we can let them come at a later time and render the page
- Specify image sizes to prevent unnecessary reflows and repaints
  - This allows for the page to not rerender the images based on runtime calculations
- Specify a Vary Accept-Encoding header
  - Prevent a bug on older browsers that don’t support compression from being served compressed versions of assets

### 3. Consider these to achieve maximum scores

- Minify HTML
  - Load less characters
- Combine possible JS and CSS to reduce number of requests
  - Having less requests from separate files also improves speed

## LICENSE

[MIT License](https://opensource.org/licenses/MIT) - [PICUS](https://picuscreative.com)
