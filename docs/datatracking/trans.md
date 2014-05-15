---
layout: page
title: Transaction Object
---

The __Transaction__ object describes first-part information associated with a
recently completed transaction. It should be used only on a checkout
confirmation page, or another page which immediately follows a transaction
occurring.

| JSON key    | Type           | Description |
|-                                           |
| order\_id               | String  | _Required_. A unique identifier for the transaction |
| currency                | String  | _Required_. The [ISO 4217](http://en.wikipedia.org/wiki/ISO_4217) code for the currency type used in this transaction, e.g. `USD`,`GBP`,`EUR` |
| subtotal                | Number  | _Required_. The total amount of the transaction, before shipping costs or discounts have been applied |
| subtotal\_includes\_tax | Boolean | `true` if `subtotal` includes the tax. |
| tax                     | Number  | The total amount of tax charged to this transaction. |
| shipping\_cost          | Number  | The shipping cost of items in this transaction. |
| shipping\_method        | String  | Delivery method for items in this transaction. |
| total                   | Number  | _Required_. The total amount of the transaction, after shipping and discounts have been applied. |
| delivery                | [Address Object](#address-object) | The destination this transaction is shipped to, if any |
| billing                 | [Address Object](#address-object) | The billing address used for this transaction |
| line\_items             | Array of [LineItem Objects](#lineitem-object) | The individual items, and their quantities, in this transaction. One LineItem per product. |

A __Transaction__ object will look something like the below example. It is not
necessary to fill any field not marked "Required".

{% highlight javascript %}
window.__pe_omnitag = {
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
    }
};
{% endhighlight %}

Address Object
---

The __Address__ object represents a mailing address.

| JSON key    | Type           | Description |
|-                                           |
| name | String | Full name of the recipient |
| address | String | Street address (e.g. `1141 Elderberry Cir`) |
| city    | String | City |
| state   | String | State (two-letter abbreviation if in US) |
| postcode | String | Postal or ZIP code |
| country  | String | Two-letter [country code](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) (e.g. `US`)

An example of the __Address__ object can be found in the example for the
[__Transaction__](#).

LineItem Object
---

The __LineItem__ object represents a specific item in a transaction, e.g. a
single product.

| JSON key    | Type           | Description |
|-                                           |
| product | String | _Required_. A unique identifier for the product |
| quantity | Number | _Required_. The number of copies of this product in the transaction |
| subtotal | Number |
The total cost of all the copies of the product, before tax, shipping, or discounts. |
| total\_discount | Number | The size of discount applied to this particular product |

An example of the __LineItem__ object can be found in the example for the
[__Transaction__](#).
