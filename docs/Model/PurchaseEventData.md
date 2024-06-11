# # PurchaseEventData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**origin** | **string** | the domain the website, see https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin |
**order_id** | **string** | A unique identifier for the order. When you re-use the order_id it will ***not*** update the order. In other words, Tracify checks whether an order with an order_id already has been received in the past. |
**currency** | **string** | The currency of the order amount denoted with ISO 4217. |
**amount** | **string** | The total amount of the order, please use 2 decimals after the comma. Should include shipping costs. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
