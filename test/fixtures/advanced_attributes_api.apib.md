FORMAT: 1A

# Advanced Attributes API
Improving the previous [Attributes](08.%20Attributes.md) description example,
this API example describes the `Coupon` resource attributes (data structure)
regardless of the serialization format. These attributes can be later
referenced using the resource name.

These attributes are then reused in the `Retrieve a Coupon` action. Since they
describe the complete message, no explicit JSON body example is needed.

Moving forward, the `Coupon` resource data structure is then reused when
defining the attributes of the coupons collection resource – `Coupons`.

The `Create a Coupon` action also demonstrate the description of request
attributes – once defined, these attributes are implied on every `Create a
Coupon` request unless the request specifies otherwise. Apparently, the
description of action attributes is somewhat duplicate to the definition of
`Coupon` resource attributes. We will address this in the next
[Data Structures](10.%20Data%20Structures.md) example.

## API Blueprint
+ [Previous: Attributes](08.%20Attributes.md)
+ [This: Raw API Blueprint](https://raw.github.com/apiaryio/api-blueprint/master/examples/09.%20Advanced%20Attributes.md)
+ [Next: Data Structures](10.%20Data%20Structures.md)

# Group Coupons

## Coupon [/coupons/{id}]
A coupon contains information about a percent-off or amount-off discount you
might want to apply to a customer.

+ Parameters
    + id (string)

        The ID of the desired coupon.

+ Attributes (object)
    + id: 250FF (string, required)
    + created: 1415203908 (number) - Time stamp
    + percent_off: 25 (number)

        A positive integer between 1 and 100 that represents the discount the coupon will apply.

    + redeem_by (number) - Date after which the coupon can no longer be redeemed

### Retrieve a Coupon [GET]
Retrieves the coupon with the given ID.

+ Response 200 (application/json)
    + Attributes (Coupon)

## Coupons [/coupons{?limit}]

+ Attributes (array[Coupon])

### List all Coupons [GET]
Returns a list of your coupons.

+ Parameters
    + limit (number, optional)

        A limit on the number of objects to be returned. Limit can range
        between 1 and 100 items.

        + Default: `10`

+ Response 200 (application/json)
    + Attributes (Coupons)

### Create a Coupon [POST]
Creates a new Coupon.

+ Attributes (object)
    + percent_off: 25 (number)
    + redeem_by (number)

+ Request (application/json)

+ Response 200 (application/json)
    + Attributes (Coupon)
