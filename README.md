## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

## To run this demo
* Open [Matt's home page](http://richards777.com/ "Matt's Home Page") with a web browser
* The first item to look at is simply the load time of index.html
* The second item is found by clicking on the "Cam's Pizzeria" link in index.html. This will take you to pizza.html.
* In pizza.html, the optimizations are related to scrolling the scroll bar and changing the slider under the text "What size pizza would you like?"

## Changes made to index.html
1. I noticed an unclosed div element, so I decided to start with the w3 validator. I thought that invalid markup might take a little longer to parse.
2. Added media tag to print css and async to Google Analytics script.
3. Still at 28 (mobile) and 30 (desktop) for PageSpeed.  I'll optimize the images.
4. Smaller images moved mobile to 77 and desktop to 90 on PageSpeed.
5. Downloading fonts to local CSS file moved mobile to 81, desktop to 92.
6. Removing font definitions for cyrillic, vietnamese, and greek did not help.
7. Inlining all of style.css moved mobile to 87 and desktop to 94.
8. Using minified version of perfmatters.js did not change PageSpeed scores.

## Changes made to main.js for pizza.html
1. Tried pulling var items = document.querySelectorAll('.mover'); out of updatePositions (which is our hot spot).  Maybe helped a little.
2. Pulled var pizzasDiv = document.getElementById("randomPizzas"); out of the for loop where the pizzas are appended.  Doesn't seem to matter.
3. Pulled sin calculation out of item loop in updatePositions.  This dropped updatePositions from 77% to 7% in profiler.  Big change, but might not be done yet.
4. Reduced the number of math operations in updatePositions.  Not a big improvement.
5. Pulled a number of computations out of the for loop in changePizzaSizes and got the resize time down to 1.7 ms from approximately 100 ms.
6. Changed calls to querySelector to either getElementById or getElementByClassName as appropriate.
7. Dynamically calculating the number of pizzas.
8. Adjusting the pizza location with translateX style instead of writing to left directly.

