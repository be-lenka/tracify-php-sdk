# # ConversionEventData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**origin** | **string** | the domain the website, see https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin |
**conversion_id** | **string** | A unique identifier for the conversion. When you re-use the conversion_id it will ***not*** update the conversion. In other words, Tracify checks whether a conversion with an conversion_id already has been received in the past. |
**currency** | **string** | The currency of the conversion value denoted with ISO 4217. |
**value** | **string** | The total value of the conversion, please use 2 decimals after the comma. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
