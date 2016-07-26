# Deliverables

Ok, everything is done and you are ready to give results to a client. This moment is the last time when you can check and fix any issue. Here is the list of what you should do (it's minimal list, I'm sure there will be much more details about your specific project):
 1. Check all supported versions of browsers that mentioned in the specifications. At least check an appearance in the latest Chrome, Firefox, Safari, and Edge.
 2. Check all reasonable scales from 50% to 250%. Also, check an appearance with narrow screens (just make your browser's width 500px).
 3. Check if all elements are visible with switched on AdBlock Extension. Sometimes AdBlock removes elements that contain such words as "ad", "advert" and "banners" in classes, ids or URLs to resources.
 4. Check if all logs are only for production mode. There should not be unprepared debug messages in the console.
 5. Check if there are some duplicated unnecessary HTTP-requests (use "Network" tab in the Chrome DevTools panel)
 6. Check if your production build is correct. If you use some build tools like WebPack, Gulp etc and there are different development and production builds - check the last one. Sometimes after concatenation, gzipping or uglifying your scripts or styles can become broken.
