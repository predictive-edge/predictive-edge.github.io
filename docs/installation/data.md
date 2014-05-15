---
layout: docs
title: Data and Revenue Integration
---

We support further tracking of first-party data, such as user and
revenue/transaction information, via a data integration.

This can be done by assigning your data to the `__pe_omnitag` variable, like
so:

{% highlight javascript %}
window.__pe_omnitag = {
    "user": {
        "name": "Full Name",
        "username": "exampleuser123",
        "user_id": "8492834083",     // Internal user id.
        "email": "user@example.com",
        "language": "en-us",         // IETF compatible string.
        "types": ["female"]          // Arbitrary labels
    },
    "page": {
        "type": "product",       // the page is of type Product
        "environment": "production",	
    },
    "transaction": { //completed purchase, for confirmation page.
        "order_id": "WEB123456",
        "currency": "USD", //ISO 4217 code
        "subtotal": 123.00,
        "subtotal_include_tax": true,
        "tax": 10.00,
        "shipping_cost": 1.00,
        "shipping_method": "Standard Mail",
        "total": 130.00, //mandatory

        "delivery": {
            "name": "Full Name",
            "address": "1141 Elderberry Cir",
            "city": "Folsom",
            "state": "CA",
            "postcode": "95630",
            "country": "US"
        },
        "billing": {
            "name": "Full Name",
            "address": "1141 Elderberry Cir",
            "city": "Folsom",
            "state": "CA",
            "postcode": "95630",
            "country": "US"
        },
        "line_items": [{
            "product": "Product1", //mandatory
            "quantity": 1, //mandatory
            "subtotal": 30.00,
            "total_discount": 5.00
        },{
            "product": "Product2", //mandatory
            "quantity": 2, //mandatory
            "subtotal": 14.00,
        }]
    },
    "version": "1.0.0" //OmniTag version number.
};
{% endhighlight %}

Not all of this data needs to be supplied - for example, you can provide only
a `transaction` object, or only a `user` object.

A detailed specification of the OmniTag can be found
[here](/docs/datatracking).

