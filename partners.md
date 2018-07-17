# Confideal API reference

## Creating a new contract

To create a new contract, you need to redirect the user to https://app.confideal.io/create with the following parameters:

* **Mandatory:**  
  ```
    partner - your account address
  ```

* **Optional:**
  ```
    returnURL=[string] - a URL where the user will be redirected
    name=[string] - contract name
    counterparty=[string] - counterparty's account address
    agreement=[string] - contract details (applicable terms and conditions)
    pricePerUnit=[number] - price per unit
    quantity=[number] - quantity of units
    advancePaymentPct=[number] - advance payment, %% of the contract price
    closeoutPaymentPct=[number] - closeout payment, %% of the contract price
    lateFeeApply=[boolean] - enable late fee
    lateFeeRatePct=[number] - late fee, %% of the contract price
    lateFeeMaxPct=[number] - late fee, %% of the contract price
    clientsContacts=[string] - client's (buyer's) email address
    contractorsContacts=[stirng] - contractor's (seller's) email address
    arbitrationClause=[boolean] - arbitration clause switch
  ```

## Retrieving all contracts

To retrieve the list of all your contracts, send a request with the following syntax:

* **URL**

  /contracts

* **Headers**
  
  `authorization="Token your_own_token"`
  
* **Method**

  `GET`
  
* **URL Params**

  none

* **Success Response:**

  * **Code:** 200  
    ```json
      [
        {
          "address": "0x7a1ba8bf2d06272a361df125c1def8dd20f949a2",
          "advancePaymentPct": "0",
          "agreement": "dfwefwefew",
          "arbitrationClause": true,
          "client": "0x87f9fc0a58e96b6f03caad97361a3cd26b6e30de",
          "confidealFee": "0.04",
          "confidealFeePayer": 0,
          "confirmed": true,
          "contractor" "0xbca00a885d89c445928c4af7d811ab6100be5fd6",
          "creationHeight": 0,
          "creationTime": 1531483204,
          "creator": "0x87f9fc0a58e96b6f03caad97361a3cd26b6e30de",
          "hash": "0xe086e1d9e2c2482e6fba136776e0db72a163b23a9c3ddcfe72f6de1e4f508d45",
          "lateFeeInterval": null,
          "lateFeeMaxPct": "0",
          "lateFeeRatePct": "0",
          "name": "0xBCA00A885D89C445928c4Af7D811AB6100bE5FD6",
          "network": 3,
          "periodTo": 1533657600,
          "price": "4",
          "pricePerUnit": "4",
          "quantity": "1",
          "stage": 100,
          "stageTime": 1531483204,
          "total": "4.04",
          "version": "1.3.1",
        }
      ]
    ```

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  
    **Content:**  
    ```json
    {
      "Error": "Wrong credentials"
    }
    ```

* **Sample call:**

  ```js
    axios('/contracts', {
      method: 'get',
      headers: {
        authorization: 'Token R6x69wgaLrVjS9t8NIj1kaCmMYZJIUFoFccE_zFN9lI',
      },
    })
  ```

## Getting contract’s properties by its hash

To get a contract’s properties by its hash, send a request with the following options:

* **URL**

  /contracts/:hash

* **Headers**
  
  `authorization="Token your_own_token"`
  where `your_own_token` is your actual token string
  
* **Method**

  `GET`
  
* **URL Params**

  none

* **Success Response:**

  * **Code:** 200  
    ```json
      {
        "contract": {
          "address": "0x7a1ba8bf2d06272a361df125c1def8dd20f949a2",
          "advancePaymentPct": "0",
          "agreement": "dfwefwefew",
          "arbitrationClause": true,
          "client": "0x87f9fc0a58e96b6f03caad97361a3cd26b6e30de",
          "confidealFee": "0.04",
          "confidealFeePayer": 0,
          "confirmed": true,
          "contractor" "0xbca00a885d89c445928c4af7d811ab6100be5fd6",
          "creationHeight": 0,
          "creationTime": 1531483204,
          "creator": "0x87f9fc0a58e96b6f03caad97361a3cd26b6e30de",
          "hash": "0xe086e1d9e2c2482e6fba136776e0db72a163b23a9c3ddcfe72f6de1e4f508d45",
          "lateFeeInterval": null,
          "lateFeeMaxPct": "0",
          "lateFeeRatePct": "0",
          "name": "0xBCA00A885D89C445928c4Af7D811AB6100bE5FD6",
          "network": 3,
          "periodTo": 1533657600,
          "price": "4",
          "pricePerUnit": "4",
          "quantity": "1",
          "stage": 100,
          "stageTime": 1531483204,
          "total": "4.04",
          "version": "1.3.1",
        },
        "claims": []
      }
    ```

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  
    **Content:**  
    ```json
    {
      "Error": "Wrong credentials"
    }
    ```

* **Sample call:**

  ```js
    axios('/contracts/0x9a277a239d4fb4b1043d5852d5e06b53958d78798e39c34a34ecd69b57a02cec', {
      method: 'get',
      headers: {
        authorization: 'Token R6x69wgaLrVjS9t8NIj1kaCmMYZJIUFoFccE_zFN9lI',
      },
    })
  ```
