## Website Performance Optimization portfolio project 4


### Getting started

####Part 1: PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. To inspect the site, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder (either SRC of DIST folder)
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder (either SRC of DIST folder)
  $> ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! 

ie

http://630c3504.ngrok.com/index.html (SRC folder)
http://630c3504.ngrok.com/index.min.html (DIST folder)

==================================================================================

Changes made to optimize this project.

1. Index.html
	- Inlined the style.css stop the css blocking
	- Used media = "print" query in line #65 to let the browser know it is only needed for printing
	- async to call to the .js files line #76 and #77
	- used the webfont script loader recommended by Google to improve speed of google web fonts and also placed at the end of the HTML file
	- Optimized all pictures using http://www.imageoptimizer.net and https://compressor.io/ to resize and compress images to improve load times

2. pizza.html (main.js)
**acknowledgement

Used these links from the forum and office hours to help optimize 60 FPS

https://discussions.udacity.com/t/still-below-60fps-when-scrolling-due-to-painting-even-though-i-did-all-the-optimization-please-help/36979/4

fend-office-hours/Web Optimization/Effective Optimizations for 60 FPS/README.md

Also from the recommendations by the reviewer of my first submission
**

	- changed function changePizzaSizes() using the switch statement at the suggestion of Cameron in Lecture Browser Rendering Optimization Lesson 5: Stop FSL
	- replaced document.querySelector() to document.getElementById() and document.querySelectorAll() to document.getElementsByClassName(), this web API call is faster.
	- modified function updatePositions() at the recommendations of many in the forums by calculating the phase value outside the loop into an array.
	- line 479 placed randomPizzas.length in local var len so the array length property is not checked every iteration.
	- line 596 dynamically calculated the number of pizzas needed in the background based on the browser window resolution using window.screen.height to calcualte the row value 
	- line 594 moved var elem ouside main loop so it will created only once
	- line 500 pizassDiv moved outside the loop to reduce call to once
function updatePositions()
	- used requestAnimationFrame at suggestions in the forum to improve smoothness of animation
	- line 565 used transform: translateX() to improve efficiency as recommended in the office hours
	- decreasing calls in the loop by moving variables out side the loop when possible

3. pizza.html (style.css)
	- At the recommendation of the first submission review added transform: translateZ(0) and backface-visibility: hidden in the .mover line 32to increase performance with hardware accelerated CSS.

4. Tools used to minify files

	- Used www.willpeavy.com / minifier / for HTML file
	- Used http://www.danstools.com/ to minfy CSS and Javascipt files

