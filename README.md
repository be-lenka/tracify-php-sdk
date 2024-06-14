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
$config = \belenka\tracify\Configuration::getDefaultConfiguration()->setApiKey('tracify-token', '<YOUR_API_KEY>');
$apiInstance = new \belenka\tracify\Api\EventsApi(new \GuzzleHttp\Client(), $config);
```

```php
// Page view event
$eventPageView = new \belenka\tracify\Model\PageViewEvent();
$eventPageView->setUrl('<SOURCE_URL>');
$eventPageView->setCustomerSiteId('<YOUR_CSID>');
$eventPageView->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('8.8.8.8') => \belenka\tracify\Model\IdentityClassification::IP_ADDRESS,
    \belenka\tracify\Model\Event::hashValue($_SERVER['HTTP_USER_AGENT']) => \belenka\tracify\Model\IdentityClassification::USER_AGENT
]);
$eventPageView->setDatetime(date('Y-m-d H:i:s'));
$eventPageView->setData(['origin' => 'https://www.example.com']);
$eventPageView->setType('pageview');
```

```php
// Product view event
$eventProductView = new \belenka\tracify\Model\ProductViewEvent();
$eventProductView->setUrl('<SOURCE_URL>');
$eventProductView->setCustomerSiteId('<YOUR_CSID>');
$eventProductView->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('8.8.8.8') => \belenka\tracify\Model\IdentityClassification::IP_ADDRESS
]);
$eventProductView->setDatetime(date('Y-m-d H:i:s'));
$eventProductView->setData(['origin' => 'https://www.example.com']);
$eventProductView->setType('productview');
```

```php
// Add to cart event
$eventAddToCart = new \belenka\tracify\Model\AddToCartEvent();
$eventAddToCart->setUrl('<SOURCE_URL>');
$eventAddToCart->setCustomerSiteId('<YOUR_CSID>');
$eventAddToCart->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('8.8.8.8') => \belenka\tracify\Model\IdentityClassification::IP_ADDRESS
]);
$eventAddToCart->setDatetime(date('Y-m-d H:i:s'));
$eventAddToCart->setData(['origin' => 'https://www.example.com']);
$eventAddToCart->setType('addtocart');
```

```php
// Purchase event
$eventPurchase = new \belenka\tracify\Model\PurchaseEvent();
$eventPurchase->setType('purchase');
$eventPurchase->setUrl('<SOURCE_URL>');
$eventPurchase->setCustomerSiteId('<YOUR_CSID>');
$eventPurchase->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('test+dev@example.com') => \belenka\tracify\Model\IdentityClassification::EMAIL,
    \belenka\tracify\Model\Event::hashValue('8.8.8.8') => \belenka\tracify\Model\IdentityClassification::IP_ADDRESS
]);
$eventPurchase->setDatetime(date('Y-m-d H:i:s'));
$eventData = new \belenka\tracify\Model\PurchaseEventData([
  'origin' => 'https://www.example.com',
  'order_id' => '<ORDER_ID>',
  'currency' => '<CURRENCY_THREE_LETTER_CODE>',
  'value' => round('<ORDER_TOTAL_PRICE>', 2)
]);
$eventPurchase->setData($eventData->toArray());
```

```php
// Conversion event
$eventConversion = new \belenka\tracify\Model\ConversionEvent();
$eventConversion->setType('conversion');
$eventConversion->setUrl('<SOURCE_URL>');
$eventConversion->setCustomerSiteId('<YOUR_CSID>');
$eventConversion->setIdentityData([
    \belenka\tracify\Model\Event::hashValue('test+dev@example.com') => \belenka\tracify\Model\IdentityClassification::EMAIL,
    \belenka\tracify\Model\Event::hashValue('8.8.8.8') => \belenka\tracify\Model\IdentityClassification::IP_ADDRESS
]);
$eventConversion->setDatetime(date('Y-m-d H:i:s'));
$eventData = new \belenka\tracify\Model\ConversionEventData([
  'origin' => 'https://www.example.com',
  'conversion_id' => '<CONVERSION_ID>',
  'currency' => '<CURRENCY_THREE_LETTER_CODE>',
  'value' => round('<ORDER_TOTAL_PRICE>', 2)
]);
$eventConversion->setData($eventData->toArray());
```

```php
// Send bulk events
try {
    $result = $apiInstance->eventsApiV1CreateEvent([
      'events' => [
        $eventPageView->toArray(),
        $eventProductView->toArray(),
        $eventAddToCart->toArray(),
        $eventPurchase->toArray(),
        $eventConversion->toArray()
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

