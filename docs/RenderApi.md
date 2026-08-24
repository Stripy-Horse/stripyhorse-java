# RenderApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**renderZpl**](RenderApi.md#renderZpl) | **POST** /v1/render | Render ZPL to PNG images |
| [**renderZplPng**](RenderApi.md#renderZplPng) | **POST** /v1/render.png | Render ZPL and return the first label as a raw PNG |


<a id="renderZpl"></a>
# **renderZpl**
> RenderOutputBody renderZpl(renderInputBody)

Render ZPL to PNG images

Renders every label in the ZPL stream. For a raw PNG of a single label use renderZplPng.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $render &#x3D; new StripyHorse\\Api\\RenderApi(null, $config); $out &#x3D; $render-&gt;renderZpl(new StripyHorse\\Model\\RenderInputBody([     &#39;zpl&#39; &#x3D;&gt; &#39;^XA^FO50,50^A0N,45,45^FDHello^FS^XZ&#39;, &#39;preset&#39; &#x3D;&gt; &#39;4x6&#39;, ])); file_put_contents(&#39;label.png&#39;, base64_decode($out-&gt;getLabels()[0]-&gt;getPng())); &#x60;&#x60;&#x60;  **curl**: &#x60;&#x60;&#x60;bash curl https://api.stripyhorse.io/v1/render \\   -H \&quot;X-Api-Key: sh_live_YOUR_KEY\&quot; -H \&quot;Content-Type: application/json\&quot; \\   -d &#39;{\&quot;zpl\&quot;:\&quot;^XA^FO50,50^A0N,45,45^FDHello^FS^XZ\&quot;,\&quot;preset\&quot;:\&quot;4x6\&quot;}&#39;  &#x60;&#x60;&#x60;

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

curl-friendly variant: the X-Label-Count response header carries the total label count.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $png &#x3D; (new StripyHorse\\Api\\RenderApi(null, $config))     -&gt;renderZplPng(new StripyHorse\\Model\\RenderInputBody([&#39;zpl&#39; &#x3D;&gt; $zpl, &#39;preset&#39; &#x3D;&gt; &#39;4x6&#39;])); &#x60;&#x60;&#x60;  **curl**: &#x60;&#x60;&#x60;bash curl https://api.stripyhorse.io/v1/render.png \\   -H \&quot;X-Api-Key: sh_live_YOUR_KEY\&quot; -H \&quot;Content-Type: application/json\&quot; \\   -d &#39;{\&quot;zpl\&quot;:\&quot;^XA^FO50,50^A0N,45,45^FDHello^FS^XZ\&quot;,\&quot;preset\&quot;:\&quot;4x6\&quot;}&#39; -o label.png &#x60;&#x60;&#x60;

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

