# RenderApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**preflightLabel**](RenderApi.md#preflightLabel) | **POST** /v1/preflight | Grade a label&#39;s barcodes before they ship |
| [**renderZpl**](RenderApi.md#renderZpl) | **POST** /v1/render | Render ZPL to PNG images |
| [**renderZplPng**](RenderApi.md#renderZplPng) | **POST** /v1/render.png | Render ZPL and return the first label as a raw PNG |


<a id="preflightLabel"></a>
# **preflightLabel**
> PreflightOutputBody preflightLabel(preflightInputBody)

Grade a label&#39;s barcodes before they ship

Renders the ZPL and grades every barcode the way a verifier grades a printed label: round-trip decode, measured module width in printer dots, dot-grid alignment (catches rasterized barcodes), quiet zones in modules, physical X-dimension against the spec minimum, blur tolerance, and a cross-density table - plus static lint findings (structure, encoding traps, out-of-bounds fields). Grade fail means a scanner will reject it; fix it before a truck does.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.RenderApi;

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

    RenderApi apiInstance = new RenderApi(defaultClient);
    PreflightInputBody preflightInputBody = new PreflightInputBody(); // PreflightInputBody | 
    try {
      PreflightOutputBody result = apiInstance.preflightLabel(preflightInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RenderApi#preflightLabel");
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
| **preflightInputBody** | [**PreflightInputBody**](PreflightInputBody.md)|  | |

### Return type

[**PreflightOutputBody**](PreflightOutputBody.md)

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

<a id="renderZpl"></a>
# **renderZpl**
> RenderOutputBody renderZpl(renderInputBody)

Render ZPL to PNG images

Renders every label in the ZPL stream. For a raw PNG of a single label use renderZplPng.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.RenderApi;

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

    RenderApi apiInstance = new RenderApi(defaultClient);
    RenderInputBody renderInputBody = new RenderInputBody(); // RenderInputBody | 
    try {
      RenderOutputBody result = apiInstance.renderZpl(renderInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RenderApi#renderZpl");
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
| **renderInputBody** | [**RenderInputBody**](RenderInputBody.md)|  | |

### Return type

[**RenderOutputBody**](RenderOutputBody.md)

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

<a id="renderZplPng"></a>
# **renderZplPng**
> String renderZplPng(renderInputBody)

Render ZPL and return the first label as a raw PNG

curl-friendly variant: the X-Label-Count response header carries the total label count.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.RenderApi;

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

    RenderApi apiInstance = new RenderApi(defaultClient);
    RenderInputBody renderInputBody = new RenderInputBody(); // RenderInputBody | 
    try {
      String result = apiInstance.renderZplPng(renderInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling RenderApi#renderZplPng");
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
| **renderInputBody** | [**RenderInputBody**](RenderInputBody.md)|  | |

### Return type

**String**

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  * Content-Type -  <br>  * X-Label-Count -  <br>  |
| **0** | Error |  -  |

