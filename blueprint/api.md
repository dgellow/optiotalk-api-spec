FORMAT: 1A

# GOFI Banking Service Provider API

The GOFI Connect API is simple Web API allowing developers to
programitically interact with banks via an unified interface.

# Group Banks

Resources related to available banks in the API.

## Bank Collection [/banks]

### List All Banks [GET]

+ Response 200 (application/json)

        [
            {
                "name": "Postbank Berlin",
                "country": "de",
                "bic": "PBNKDEFFXXX",
            },
            {
                "name": "UBS Switzerland",
                "country": "ch",
                "bic": "UBSWCHZH80A",
            }
        ]

# Group Bank accounts

Resources related to a user bank accounts.

## Bank accounts Collection [/accounts]

### Register a New Bank account [POST]

You may register a new bank account using this action.

+ Attributes
  + iban (string)
  + bic (string)

+ Request (application/json)

        {
            "iban": "CH150024324343241640P",
            "bic": "UBSWCHZH80A",
        }

+ Response 201 (application/json)

    + Headers

            Location: /accounts/gBnoYf07m3FuB46Oudmd3YCEVxNq

    + Body

            {
                "id": "gBnoYf07m3FuB46Oudmd3YCEVxNq",
                "latest_crawl_at": "2017-10-11T08:40:51.620Z",
                "iban": "CH150024324343241640P",
                "bic": "UBSWCHZH80A",
                "type": "current"
                "latest_transactions": [
                    {
                        "date": "2017-10-09T13:10:01.530Z",
                        "type": "maestro debit"
                        "to": "El dios del jamon",
                        "amount": "10",
                        "cents": "20",
                        "currency": "eur",
                    }
                ]
            }

## Bank account [/accounts/{account_id}]

+ Parameters
  + account_id: `gBnoYf07m3FuB46Oudmd3YCEVxNq` (string) - ID of the Bank account

### View a Bank account detail [GET]

+ Response 200 (application/json)

        {
            "id": "gBnoYf07m3FuB46Oudmd3YCEVxNq",
            "latest_crawl_at": "2017-10-11T08:40:51.620Z",
            "iban": "CH150024324343241640P",
            "bic": "UBSWCHZH80A",
            "type": "current"
            "latest_transactions": [
                {
                    "date": "2017-10-09T13:10:01.530Z",
                    "type": "maestro debit",
                    "action": "debit",
                    "name": "El dios del jamon",
                    "iban": "ES670024624383249320P",
                    "amount": "10",
                    "cents": "20",
                    "currency": "eur",
                }
            ]
        }

### Unregister [DELETE]

+ Response 204

# Group Transfers

Resources related to transfers of money between bank accounts.

## Transfers Collection [/transfers]

### Create a new transfer [POST]

+ Attributes
  + type (string)
  + to (string)
  + action (string)
  + name (string)
  + iban (string)
  + amount (string)
  + cents (string)
  + currency (string)

+ Request (application/json)

        {
            "type": "maestro debit",
            "action": "debit",
            "name": "El dios del jamon",
            "iban": "ES670024624383249320P",
            "amount": "10",
            "cents": "20",
            "currency": "eur"
        }

+ Response 201 (application/json)
    + Headers

            Location: /transfers/cSfPxwbnXgiopMZ78FjrIWWebscW

    + Body

            {
                "id": "cSfPxwbnXgiopMZ78FjrIWWebscW",
                "date": "2017-10-09T13:10:01.530Z",
                "type": "maestro debit",
                "action": "debit",
                "name": "El dios del jamon",
                "iban": "ES670024624383249320P",
                "amount": "10",
                "cents": "20",
                "currency": "eur"
            }

## Transfer [/transfers/{transfer_id}]

+ Parameters
  + transfer_id: `cSfPxwbnXgiopMZ78FjrIWWebscW` (string) - ID of the Transfer

### View a Transfer detail [GET]
+ Response 200 (application/json)

        {
            "id": "cSfPxwbnXgiopMZ78FjrIWWebscW",
            "date": "2017-10-09T13:10:01.530Z",
            "type": "maestro debit",
            "action": "debit",
            "name": "El dios del jamon",
            "iban": "ES670024624383249320P",
            "amount": "10",
            "cents": "20",
            "currency": "eur"
        }

### Cancel [DELETE]

+ Response 204
