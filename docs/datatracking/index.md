---
layout: docs
title: OmniTag Specification
---

Predictive Edge's OmniTag is a JSON object that allows you to submit, track,
and target on a wide range of first-party data.

The fields of the OmniTag are as follows:

| JSON key    | Type           | Description |
|-                                           |
| user        | [User Object](/docs/datatracking/user)         | Information associated with this particular user |
| page        | [Page Object](/docs/datatracking/page)         | Information associated with this particular page |
| transaction | [Transaction Object](/docs/datatracking/trans) | If the user has just completed a transaction, then the contents of that transaction. Should only be used on a confirmation page |

Not all the fields are required. For example, you can specify only a `user`
and not a `page`, which would allow you to perform user-related targeting but
not page-related targeting.

<!---
| product     | [Product Object](/docs/datatracking/prod)      | Information associated with the product on this particular page. Should only be used if this page is a product page. |
| basket      | [Basket Object](/docs/datatracking/basket)     | The user's current shopping cart contents |
--->


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
        "voucher": "MYVOUCHER",
        "voucher_discount": 0.00,
        "tax": 10.00,
        "shipping_cost": 1.00,
        "shipping_method": "Standard Mail",
        "total": 130.00, //mandatory

        "delivery": {
            "name": "Full Name",
            "address": "234 High Street",
            "city": "London",
            "state": "London",
            "postcode": "SW1 1AB",
            "country": "GB"
        },
        "billing": {
            "name": "Full Name",
            "address": "234 High Street",
            "city": "London",
            "state": "London",
            "postcode": "SW1 1AB",
            "country": "GB"
        },
        "line_items": [{
            "product": Product //mandatory
            "quantity": 1, //mandatory
            "subtotal": 30.00,
            "total_discount": 5.00
        }, LineItem, LineItem, ...]
    },
    "version": "1.0.0" //OmniTag version number.
};
{% endhighlight %}
