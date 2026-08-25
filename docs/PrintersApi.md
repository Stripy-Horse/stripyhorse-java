# PrintersApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**parseHostStatus**](PrintersApi.md#parseHostStatus) | **POST** /v1/host-status/parse | Decode a Zebra ~HS host status response |


<a id="parseHostStatus"></a>
# **parseHostStatus**
> HostStatusOutputBody parseHostStatus(hostStatusInputBody)

Decode a Zebra ~HS host status response

Parses the three-line ~HS answer a Zebra printer (or our virtual printer) returns on port 9100 into typed fields - paper out, pause, buffer contents, head temperature - so you never write a positional comma parser. Accepts raw bytes, cat -v style ^B/^C markers, or hand-cleaned lines. Does not count against your monthly quota.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.PrintersApi;

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

    PrintersApi apiInstance = new PrintersApi(defaultClient);
    HostStatusInputBody hostStatusInputBody = new HostStatusInputBody(); // HostStatusInputBody | 
    try {
      HostStatusOutputBody result = apiInstance.parseHostStatus(hostStatusInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling PrintersApi#parseHostStatus");
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
| **hostStatusInputBody** | [**HostStatusInputBody**](HostStatusInputBody.md)|  | |

### Return type

[**HostStatusOutputBody**](HostStatusOutputBody.md)

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

