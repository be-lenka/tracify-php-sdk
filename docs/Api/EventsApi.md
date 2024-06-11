# belenka\tracify\EventsApi

All URIs are relative to https://api.tracify.ai, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**eventsApiV1CreateEvent()**](EventsApi.md#eventsApiV1CreateEvent) | **POST** /api/v1/events | Submit new server-side events |


## `eventsApiV1CreateEvent()`

```php
eventsApiV1CreateEvent($create_events_request): \belenka\tracify\Model\CreateEventsResponse
```

Submit new server-side events

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure API key authorization: TracifyTokenAuth
$config = belenka\tracify\Configuration::getDefaultConfiguration()->setApiKey('tracify-token', 'YOUR_API_KEY');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = belenka\tracify\Configuration::getDefaultConfiguration()->setApiKeyPrefix('tracify-token', 'Bearer');


$apiInstance = new belenka\tracify\Api\EventsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_events_request = new \belenka\tracify\Model\CreateEventsRequest(); // \belenka\tracify\Model\CreateEventsRequest

try {
    $result = $apiInstance->eventsApiV1CreateEvent($create_events_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->eventsApiV1CreateEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_events_request** | [**\belenka\tracify\Model\CreateEventsRequest**](../Model/CreateEventsRequest.md)|  | |

### Return type

[**\belenka\tracify\Model\CreateEventsResponse**](../Model/CreateEventsResponse.md)

### Authorization

[TracifyTokenAuth](../../README.md#TracifyTokenAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
