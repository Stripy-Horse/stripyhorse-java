# ComposeApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**composeLabel**](ComposeApi.md#composeLabel) | **POST** /v1/labels/compose | Compose ZPL from typed JSON elements |


<a id="composeLabel"></a>
# **composeLabel**
> ComposeOutputBody composeLabel(composeInputBody)

Compose ZPL from typed JSON elements

Labels as JSON: place text, barcodes (code128/39, QR, DataMatrix), boxes, lines, circles, images and raw ZPL passthrough on a label and get back ZPL - optionally with rendered previews. {{name}} in text/data interpolates from the variables map; an unresolved variable is an error, never a blank on a real shipment. Positions are printer dots.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ComposeApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.stripyhorse.io");
    
    // Configure API key authorization: headerKey
    ApiKeyAuth headerKey = (ApiKeyAuth) defaultClient.getAuthentication("headerKey");
    headerKey.setApiKey("YOUR API KEY");
    // Uncomment the following line to set a prefix for the API key, e.g. "Token" (defaults to null)
    //headerKey.setApiKeyPrefix("Token");

    // Configure HTTP bearer authorization: bearerKey
    HttpBearerAuth bearerKey = (HttpBearerAuth) defaultClient.getAuthentication("bearerKey");
    bearerKey.setBearerToken("BEARER TOKEN");

    ComposeApi apiInstance = new ComposeApi(defaultClient);
    ComposeInputBody composeInputBody = new ComposeInputBody(); // ComposeInputBody | 
    try {
      ComposeOutputBody result = apiInstance.composeLabel(composeInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ComposeApi#composeLabel");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **composeInputBody** | [**ComposeInputBody**](ComposeInputBody.md)|  | |

### Return type

[**ComposeOutputBody**](ComposeOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

