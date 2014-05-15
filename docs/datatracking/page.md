---
layout: page
title: Page Object
---

The __Page__ object describes first-party information associated with the
current page.

| JSON key    | Type           | Description |
|-                                           |
| type        | String | The type of page represented. Can be any string, but `landing`, `category`, `product`, `basket`, `checkout`, and `confirmation` are recommended, as we provide some special functionality for those page types |
| environment | String | A name for the environment which is serving this page, e.g. `production`, `testing` |

A __Page__ object will look something like the below example. It is not
necessary to fill any or all of the fields - however, we can only target and
make recommendations on fields that you have filled out.

{% highlight javascript %}
window.__pe_omnitag = {
  "page": {
      "type": "landing",
      "environment: "production"
  }
  // more fields
};
{% endhighlight %}

