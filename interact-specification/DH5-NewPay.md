# HEP Node API

## Basic Parameters: 

| Field | Type | Notes |
| --- | --- | --- |
| dapp_id | string | Decentralized Application Id |
| uuid | string | request uuid |
| protocol | string | protocol name. The default is "HEP". |
| version | string    | protocol version. The example is "1.0". |
| ts | number | timestamp |
| nonce | string | random string or auto-increment sequence |

The timestamp and nonce fields is for preventing the replay attack.


## Union Login

### Steps

1. DH5 app 
calls the js function **hep.login** with basic parameters and extra parameters, such as scope, expired, memo, sign_type and signature.
2. NewPay sends **dapp_profile** to verify DH5 app info.
3. NewPay authorizes Login.
4. NewPay sends profile back to DH5 app.

### hep.login

#### Parameters + Basic Parameters(Top of the page)

| Field | Type | Notes |
| --- | --- | --- |
| scope  | int    | profile type Id. 1: base profile including name,head,newid; 2: advance profile including cellphone  |
| expired | number | Expired timestamp. |
| memo | string | Login Memo,optional |
| sign_type | string | Signature Type,aka cryptographic algorithm |
| signature | string | signature hex string by application owner, format: "0xf9559857bb89e106de1c97bf640a481ff77a6f51e9ba8e8487d43999af0369c4e89eecca9ae085c44506137bc12ef16b24347c6b93b04fee5ef8572818382138". |
| success | function | callback function for successfully aquiring profile |
| fail | function | callback function for failling to aquire profile|

#### Example Parameters
TBD

#### Returns
| Field | Type | Notes |
| --- | --- | --- |
| name | string | name |
| newid | string | NewID |
| wallet_address | string | wallet address |
| avatar | string | avatar |
| public_key | string | public key |
| country_code | string | country code |
| cellphone | string | cellphone |


#### Example
TBD


### dapp_profile
Verify the dapp information
Details in [REST-API]

*** 

## Payment

### Steps

1. DH5 app calls the js function **hep.pay** with basic parameters and extra parameters, such as expired, description, price_currency, total_price, order_number, seller, customer, broker, signature.
2. NewPay sends **dapp_profile** to verify DH5 app info.
3. NewPay authorizes and makes the payment.
4. NewPay sends profile back to DH5 app.


### hep.pay

#### Parameters + Basic Parameters(Top of the page)

| Field            | Type   | Notes                                      |
| ---              | ---    | ---                                        |
| expired          | number | Expired timestamp                             |
| description      | string | The order description |
| price_currency   | string | symbol of fiat or digital token, such as USD, RMB, NEW,BTC,ETH
| total_price      | string | amount of fiat or digital token, unit is the minimum unit of given fiat or digital token |
| order_number     | string | The order number. |
| seller           | string | The seller's NewID  |
| customer         | string | The customer's NewID |
| broker           | string | The broker's NewID. optional.  |
| signature        | string | signature hex string by application owner, format: "secp256r1:0xf9559857bb89e106de1c97bf640a481ff77a6f51e9ba8e8487d43999af0369c4e89eecca9ae085c44506137bc12ef16b24347c6b93b04fee5ef8572818382138". |
| success | function | callback function for successfully aquiring profile |
| fail | function | callback function for failling to aquire profile|


#### Example Parameters
TBD

#### Returns
success / fail

#### Example
TBD

### dapp_profile
Verify the dapp information
Details in [REST-API]

***

## Proof

### Steps

1. DH5 app calls the js function **hep.submitProof** with basic parameters and extra parameters, such as description, price_currency, total_price, order_number, order_items, seller, customer, broker, signature.
2. NewPay sends **dapp_profile** to verify DH5 app info.
3. NewPay authorizes and submits the proof.
4. NewPay notify success/fail back to DH5 app.

### hep.submitProof

#### Parameters + Basic Parameters(Top of the page)

| Field            | Type   | Notes                                      |
| ---              | ---    | ---                                        |
| description      | string | The order description |
| price_currency   | string | symbol of fiat or digital token, such as USD, RMB, NEW,BTC,ETH
| total_price      | string | amount of fiat or digital token, unit is the minimum unit of given fiat or digital token |
| order_number     | string | The order number. |
| order_items      | json | The list of order items, see [schema/order-item.json]. |
| seller           | string | The seller's NewID  |
| customer         | string | The customer's NewID |
| broker           | string | The broker's NewID. optional.  |
| signature        | string | signature hex string by application owner, format: "secp256r1:0xf9559857bb89e106de1c97bf640a481ff77a6f51e9ba8e8487d43999af0369c4e89eecca9ae085c44506137bc12ef16b24347c6b93b04fee5ef8572818382138". |
| success | function | callback function for successfully aquiring profile |
| fail | function | callback function for failling to aquire profile|

### dapp_profile
Verify the dapp information
Details in [REST-API]
