---
layout: page
title: User Object
---

The __User__ object describes first-party information associated with the
current visitor or logged-in user.

| JSON key    | Type           | Description |
|-                                           |
| name     | String | The full real name of a user               |
| username | String | The identifier the user provides to log in |
| user\_id | String | A unique identifier that the website uses internally to identify the user |
| email    | String | The user's email address. May be the same as `username` |
| language | String | The user's preferred language. Should be [IETF-compatible](http://en.wikipedia.org/wiki/IETF_language_tag) |
| types    | Array  | An array consisting of strings that identify this user, e.g. `["female", "18-25"]`. There can be any number of these, and there are no restrictions on what strings may be used. |

A __User__ object will look something like the below example. It is not necessary to fill
any or all of the fields - however, we can only target and make
recommendations on fields that you have filled out.

{% highlight javascript %}
window.__pe_omnitag = {
  "user": {
      "name": "Full Name",
      "username": "exampleuser123",
      "user_id": "8492834083",     // Internal user id.
      "email": "user@example.com",
      "language": "en-us",         // IETF compatible string.
      "types": ["female"]          // Arbitrary labels
  }
};
{% endhighlight %}

