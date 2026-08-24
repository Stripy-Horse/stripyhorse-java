# ConvertApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**convertBatch**](ConvertApi.md#convertBatch) | **POST** /v1/convert/batch | Convert many documents in one request, results streamed |
| [**convertDocument**](ConvertApi.md#convertDocument) | **POST** /v1/convert | Convert a PDF or image to ZPL |
| [**convertHtml**](ConvertApi.md#convertHtml) | **POST** /v1/convert/html | Convert an HTML label design to ZPL |
| [**convertZplToHtml**](ConvertApi.md#convertZplToHtml) | **POST** /v1/convert/zpl-html | Decompile ZPL into editable HTML |
| [**voidZpl**](ConvertApi.md#voidZpl) | **POST** /v1/void | Stamp ZPL as void / do-not-ship |


<a id="convertBatch"></a>
# **convertBatch**
> convertBatch(files, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm)

Convert many documents in one request, results streamed

Upload up to 20 PDFs/images as repeated &#x60;files&#x60; fields. The response is application/x-ndjson: one JSON object per converted page, streamed as each page finishes — &#x60;{\&quot;file\&quot;:…,\&quot;page\&quot;:…,\&quot;pageCount\&quot;:…,\&quot;zpl\&quot;:…}&#x60; on success, &#x60;{\&quot;file\&quot;:…,\&quot;error\&quot;:…}&#x60; per failed file (remaining files still convert).

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ConvertApi;

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

    ConvertApi apiInstance = new ConvertApi(defaultClient);
    List<File> files = Arrays.asList(); // List<File> | 
    Boolean barcodeAware = true; // Boolean | 
    String compression = "compression_example"; // String | 
    Long dpmm = 56L; // Long | 
    Double heightMm = 3.4D; // Double | 
    String preset = "preset_example"; // String | 
    Long rotation = 56L; // Long | 
    String scale = "scale_example"; // String | 
    Long threshold = 56L; // Long | 
    Double widthMm = 3.4D; // Double | 
    try {
      apiInstance.convertBatch(files, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
    } catch (ApiException e) {
      System.err.println("Exception when calling ConvertApi#convertBatch");
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
| **files** | **List&lt;File&gt;**|  | |
| **barcodeAware** | **Boolean**|  | [optional] |
| **compression** | **String**|  | [optional] |
| **dpmm** | **Long**|  | [optional] |
| **heightMm** | **Double**|  | [optional] |
| **preset** | **String**|  | [optional] |
| **rotation** | **Long**|  | [optional] |
| **scale** | **String**|  | [optional] |
| **threshold** | **Long**|  | [optional] |
| **widthMm** | **Double**|  | [optional] |

### Return type

null (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="convertDocument"></a>
# **convertDocument**
> ConvertOutputBody convertDocument(_file, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm)

Convert a PDF or image to ZPL

Each page becomes its own ^GFA command (Zebra ACS run-length compression). PDFs up to 16 pages.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ConvertApi;

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

    ConvertApi apiInstance = new ConvertApi(defaultClient);
    File _file = new File("/path/to/file"); // File | PDF, PNG, GIF or JPEG
    Boolean barcodeAware = true; // Boolean | EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization
    String compression = "compression_example"; // String | acs (default) or z64 (zlib+base64, smaller payloads)
    Long dpmm = 56L; // Long | 
    Double heightMm = 3.4D; // Double | 
    String preset = "preset_example"; // String | 
    Long rotation = 56L; // Long | 
    String scale = "scale_example"; // String | cover (fit), fill (stretch) or none
    Long threshold = 56L; // Long | 
    Double widthMm = 3.4D; // Double | 
    try {
      ConvertOutputBody result = apiInstance.convertDocument(_file, barcodeAware, compression, dpmm, heightMm, preset, rotation, scale, threshold, widthMm);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ConvertApi#convertDocument");
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
| **_file** | **File**| PDF, PNG, GIF or JPEG | |
| **barcodeAware** | **Boolean**| EXPERIMENTAL: re-emit decodable barcodes as native ^BC/^BQ fields, verified by a decode round trip with automatic fallback to plain rasterization | [optional] |
| **compression** | **String**| acs (default) or z64 (zlib+base64, smaller payloads) | [optional] |
| **dpmm** | **Long**|  | [optional] |
| **heightMm** | **Double**|  | [optional] |
| **preset** | **String**|  | [optional] |
| **rotation** | **Long**|  | [optional] |
| **scale** | **String**| cover (fit), fill (stretch) or none | [optional] |
| **threshold** | **Long**|  | [optional] |
| **widthMm** | **Double**|  | [optional] |

### Return type

[**ConvertOutputBody**](ConvertOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="convertHtml"></a>
# **convertHtml**
> HtmlOutputBody convertHtml(htmlInputBody)

Convert an HTML label design to ZPL

Renders the HTML at exact print resolution (headless Chrome, network access blocked) and rasterizes it — except &#x60;&lt;zpl-barcode type&#x3D;\&quot;code128|qr\&quot; data&#x3D;\&quot;…\&quot;&gt;&#x60; elements, which are measured from the layout and emitted as native ^BC/^BQ fields at their exact boxes. Size and position them with CSS (&#x60;left/top/width/height&#x60;); optional &#x60;module&#x60; (^BY dots) and &#x60;mag&#x60; (QR magnification) attributes pin exact bar geometry instead of fitting it to the box. Unsupported types or unencodable data fail loudly.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $out &#x3D; $convert-&gt;convertHtml(new StripyHorse\\Model\\HtmlInputBody([     &#39;html&#39; &#x3D;&gt; &#39;&lt;div style&#x3D;\&quot;position:absolute;left:40px;top:40px;font-size:50px\&quot;&gt;Hello&lt;/div&gt;&#39;,     &#39;preset&#39; &#x3D;&gt; &#39;4x6&#39;, ])); echo $out-&gt;getZpl(); &#x60;&#x60;&#x60;

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ConvertApi;

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

    ConvertApi apiInstance = new ConvertApi(defaultClient);
    HtmlInputBody htmlInputBody = new HtmlInputBody(); // HtmlInputBody | 
    try {
      HtmlOutputBody result = apiInstance.convertHtml(htmlInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ConvertApi#convertHtml");
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
| **htmlInputBody** | [**HtmlInputBody**](HtmlInputBody.md)|  | |

### Return type

[**HtmlOutputBody**](HtmlOutputBody.md)

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

<a id="convertZplToHtml"></a>
# **convertZplToHtml**
> ZplHTMLOutputBody convertZplToHtml(zplHTMLInputBody)

Decompile ZPL into editable HTML

The migration path for legacy ZPL templates: text, boxes and Code128/QR barcodes become editable HTML in the dialect convertHtml accepts; unsupported elements (raster graphics, exotic barcodes) are embedded as positioned images so the layout survives. Round-tripping through convertHtml preserves scannable barcodes.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ConvertApi;

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

    ConvertApi apiInstance = new ConvertApi(defaultClient);
    ZplHTMLInputBody zplHTMLInputBody = new ZplHTMLInputBody(); // ZplHTMLInputBody | 
    try {
      ZplHTMLOutputBody result = apiInstance.convertZplToHtml(zplHTMLInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ConvertApi#convertZplToHtml");
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
| **zplHTMLInputBody** | [**ZplHTMLInputBody**](ZplHTMLInputBody.md)|  | |

### Return type

[**ZplHTMLOutputBody**](ZplHTMLOutputBody.md)

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

<a id="voidZpl"></a>
# **voidZpl**
> VoidOutputBody voidZpl(voidInputBody)

Stamp ZPL as void / do-not-ship

Overlays large DO NOT SHIP warnings (and an optional attribution stamp) across every label in the stream, so printed dev and test labels can never be mistaken for shippable ones. Original fields are untouched; stamps draw on top.

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.ConvertApi;

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

    ConvertApi apiInstance = new ConvertApi(defaultClient);
    VoidInputBody voidInputBody = new VoidInputBody(); // VoidInputBody | 
    try {
      VoidOutputBody result = apiInstance.voidZpl(voidInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling ConvertApi#voidZpl");
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
| **voidInputBody** | [**VoidInputBody**](VoidInputBody.md)|  | |

### Return type

[**VoidOutputBody**](VoidOutputBody.md)

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

