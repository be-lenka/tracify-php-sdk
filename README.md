# Tracify.dev PHP SDK

This API allows you to send events to Tracify that originate from
your server.

## Installation & Usage

### Requirements

PHP 7.4 and later.
Should also work with PHP 8.0.

### Composer

To install the bindings via [Composer](https://getcomposer.org/), add the following to `composer.json`:

```json
{
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/be-lenka/tracify-php-sdk.git"
    }
  ],
  "require": {
    "be-lenka/tracify-php-sdk": "*@dev"
  }
}
```

Then run `composer install`


## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure API key authorization: TracifyTokenAuth
$config = belenka\tracify\Configuration::getDefaultConfiguration()->setApiKey('tracify-token', '<YOUR_API_KEY>');
// Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
// $config = belenka\tracify\Configuration::getDefaultConfiguration()->setApiKeyPrefix('tracify-token', 'Bearer');

$apiInstance = new \belenka\tracify\Api\EventsApi(new \GuzzleHttp\Client(), $config);

$event = new \belenka\tracify\Model\ProductViewEvent();
$event->setUrl('<SOURCE_URL>');
$event->setCustomerSiteId('<YOUR_CSID>');
$event->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('test+dev@example.com') => \belenka\tracify\Model\IdentityClassification::EMAIL
]);
$event->setDatetime(date('Y-m-d H:i:s'));
$event->setData(['origin' => 'https://www.example.com']);
$event->setType('productview');

try {
    $result = $apiInstance->eventsApiV1CreateEvent([
      'events' => [
        $event->toArray()
      ]
    ]);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EventsApi->eventsApiV1CreateEvent: ', $e->getMessage(), PHP_EOL;
}

```

## API Endpoints

All URIs are relative to *https://api.tracify.ai*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*EventsApi* | [**eventsApiV1CreateEvent**](docs/Api/EventsApi.md#eventsapiv1createevent) | **POST** /api/v1/events | Submit new server-side events

## Models

- [AddToCartEvent](docs/Model/AddToCartEvent.md)
- [BaseEvent](docs/Model/BaseEvent.md)
- [BaseEventData](docs/Model/BaseEventData.md)
- [ConversionEvent](docs/Model/ConversionEvent.md)
- [ConversionEventData](docs/Model/ConversionEventData.md)
- [CreateEventsRequest](docs/Model/CreateEventsRequest.md)
- [CreateEventsResponse](docs/Model/CreateEventsResponse.md)
- [Event](docs/Model/Event.md)
- [IdentityClassification](docs/Model/IdentityClassification.md)
- [PageViewEvent](docs/Model/PageViewEvent.md)
- [PageViewEventData](docs/Model/PageViewEventData.md)
- [PostPurchaseSurveyEvent](docs/Model/PostPurchaseSurveyEvent.md)
- [PostPurchaseSurveyEventData](docs/Model/PostPurchaseSurveyEventData.md)
- [ProductViewEvent](docs/Model/ProductViewEvent.md)
- [PurchaseEvent](docs/Model/PurchaseEvent.md)
- [PurchaseEventData](docs/Model/PurchaseEventData.md)

## Authorization

Authentication schemes defined for the API:
### TracifyTokenAuth

- **Type**: API key
- **API key parameter name**: tracify-token
- **Location**: HTTP header


## Tests

To run the tests, use:

```bash
composer install
vendor/bin/phpunit
```

