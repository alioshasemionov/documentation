# Documentation

## Show a dashboard

Shows all contracts

* **URL**

  /
  
* **URL Params**

  none

## Open create contract form

Opens create contract form

* **URL**

  /create
  
* **URL Params**

  ```
    counterparty=[string]
    name=[string]
    agreement=[string]
    periodToDate=[string]
    periodToHour=[stirng]
    pricePerUnit=[string]
    quantity=[string]
    price=[string]
    advancePaymentPct=[number]
    closeoutPaymentPct=[number]
    lateFeeApply=[bool]
    lateFeeRatePct=[number]
    lateFeeMaxPct=[number]
    clientsContacts=[string]
    contractorsContacts=[string]
    arbitrationClause=[bool]
    partnerId=[string]
    returnURL=[string]
  ```

## Show contract data

Show contract data by a hash

* **URL**

  /details/:hash

---

## Get networks

Returns a json array of numbers.

* **URL**

  /networks

* **Headers**
  
  none
  
* **Method**

  `GET`
  
* **URL Params**

  none

* **Success Response:**

  * **Code:** 200  

* **Error Response:**  

  * **Code:** 500 INTERNAL SEVER ERROR
    ```json
      {
        "Error": "Internal Server Error"
      }
    ```

## Login

Returns a json object with an authToken and an expiration.

* **URL**

  /login

* **Headers**
  
  `signature`  
  `timestamp`
  
* **Method**

  `POST`
  
* **URL Params**

  none

* **Success Response:**

  * **Code:** 200  

* **Error Response:**
  * **Code:** 401 UNAUTHORIZED
  * **Content:**  
    ```json
      {
        "Error": "Wrong credentials"
      }
    ```

## Get minArbitrationFee

Returns a minArbitrationFee value.

* **URL**

  /minArbitrationFee

* **Headers**
  
  `authorization`
  
* **Method**

  `GET`
  
* **URL Params**

  `network=[number]`

* **Success Response:**

  * **Code:** 200  

* **Error Response:**
  * **Code:** 500 INTERNAL SEVER ERROR
    ```json
      {
        "Error": "Internal Server Error"
      }
    ```

## Create a new contract

Creates new contract.

* **URL**

  /network/:network/account/:account/contracts


* **Headers**
  
  `authorization`
  
* **Method**

  `POST`
  
* **URL Params**

   ```
    "network"=[number]
    "version"=[string]
    "name"=[string]
    "stage"=[number]
    "creator"=[string]
    "client"=[string]
    "contractor"=[string]
    "agreement"=[string]
    "pricePerUnit"=[string]
    "quantity"=[string]
    "price"=[string]
    "advancePaymentPct"=[string]
    "periodTo"=[number]
    "confidealFeePayer"=[number]
    "creatorGaId"=[string]
    "clientsContacts"=[string]
    "contractorsContacts"=[string]
    "arbitrationClause"=[number]
    "lateFeeRatePct"=[string]
    "lateFeeInterval"=[string]
    "lateFeeMaxPct"=[string]
    "partnerId"=[string]
   ```

* **Success Response:**

  * **Code:** 200  

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Load contracts

Returns json data about an user's contracts.

* **URL**

  /network/:network/accounts/:account/contracts

* **Headers**
  
  `authorization`
  
* **Method**

  `GET`
  
* **URL Params**

   None

* **Success Response:**

  * **Code:** 200  
    **Content:**
    ```
    {
      "hash": "0x3cd00494623d4d406b468e3baebcf60a95cba4250ec325e0530531278859c97b",
      ...
    }
    ```

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Load a contract

Returns json data about a contract by a hash.

* **URL**

  /contracts/:hash

* **Headers**
  
  `authorization`
  
* **Method**

  `GET`
  
* **URL Params**

   None

* **Success Response:**

  * **Code:** 200  
    **Content:**
    ```
    [
      "contract": {
        "hash": "0x3cd00494623d4d406b468e3baebcf60a95cba4250ec325e0530531278859c97b",
        ...
      },
      "claims": [
        {
          "hash": "0x1d1f4b1aa1385cbc38645644f108b62db58e6dbff8faa78d725cf864bcacb0db",
          ...
        }
      ],
    ]
    ```

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Update a contract

Updates a contract by a hash.

* **URL**

  /contracts/:hash

* **Headers**
  
  `authorization`
  
* **Method**

  `PATCH`
  
* **URL Params**

   None

* **Success Response:**

  * **Code:** 200  
    **Content:**
    `success`

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Delete a contract

Deletes a contract by a hash.

* **URL**

  /contracts/:hash

* **Headers**
  
  `authorization`
  
* **Method**

  `DELETE`
  
* **URL Params**

   None

* **Success Response:**

  * **Code:** 200  
    **Content:**
    `success`

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Add/reject a contract

Adds/rejects a contract by a hash.

* **URL**

  /contracts/:hash/meta

* **Headers**
  
  `authorization`
  
* **Method**

  `POST`
  
* **URL Params**

   ```
    "name"=[string]
   ```

* **Success Response:**

  * **Code:** 200  
    **Content:**
    `success`

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Create new claim

Adds a claim

* **URL**

  /contracts/:hash/claims

* **Headers**
  
  `authorization`
  
* **Method**

  `POST`
  
* **URL Params**

   ```
    "text"=[string]
    "accountAddress"=[string]
    "contractHash"=[string]
   ```

* **Success Response:**

  * **Code:** 200  
    **Content:**
    `success`

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  

## Add a resolution

Adds a resolution

* **URL**

  /contracts/:hash/resolutions

* **Headers**
  
  `authorization`
  
* **Method**

  `POST`
  
* **URL Params**

   ```
    "arbiter"=[string]
    "resolutionHash"=[string]
    "resolutionTime"=[number]
    "contractHash"=[number]
    "resolutionMessage"=[string]
    "clientShare"=[string]
    "contractorShare"=[string]
   ```

* **Success Response:**

  * **Code:** 200  
    **Content:**
    `success`

* **Error Response:**

  * **Code:** 401 UNAUTHORIZED  
