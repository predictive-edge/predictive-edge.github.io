---
layout: page
title: Installing the Tag
---

There are two possible tags you can install - a __synchronous__ tag and an
__asynchronous__ one. Each has advantages and disadvantages. You can find both of them
on [your dashboard](http://dashboard.predictiveedge.com/app/settings/integration).

Synchronous Tag
---
The synchronous tag must be downloaded before the rest of your page renders.
Doing so helps minimize the occurence of flicker for any targeted
variations you might make; however it will slightly impact the load time of
your site (10-30ms).

Asynchronous Tag
---
The asynchronous tag will minimize the impact on your page's load times.
However, it can sometimes cause noticeable flickering if large images are
replaced.

Installing
---
Paste the provided tag into your website template page so that it appears
before closing the </head> tag. The code snippet should be before any page
content and before any Google Analytics tracking code; this helps minimize any
flickering that might occur for edited variations.



