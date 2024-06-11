# # PageViewEventData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**origin** | **string** | the domain the website, see https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin |
**url_parameters** | **string** | pass **each** URL parameter as a key-value pair. Must be passed on the first event of a session in order to attribute correctly  Landing page example: &#x60;https://www.example.com?utm_source&#x3D;newsletter&amp;utm_medium&#x3D;email&amp;trc_mcmp_id&#x3D;111&amp;trc_mag_id&#x3D;222&amp;trc_mad_id&#x3D;333&#x60;  In this example pass five key-values in the data object  &#x60;\&quot;utm_source\&quot;: \&quot;newsletter\&quot;&#x60;  &#x60;\&quot;utm_medium\&quot;: \&quot;email\&quot;&#x60;  &#x60;\&quot;trc_mcmp_id\&quot;: \&quot;111\&quot;&#x60;  &#x60;\&quot;trc_mag_id\&quot;: \&quot;222\&quot;&#x60;  &#x60;\&quot;trc_mad_id\&quot;: \&quot;333\&quot;&#x60;  See also https://en.wikipedia.org/wiki/Query_string. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
