# SimulatorApi

All URIs are relative to *https://api.stripyhorse.io*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**clearJobs**](SimulatorApi.md#clearJobs) | **DELETE** /v1/printers/{printerId}/jobs | Delete all captured jobs |
| [**createPrinter**](SimulatorApi.md#createPrinter) | **POST** /v1/printers | Create a virtual printer |
| [**deletePrinter**](SimulatorApi.md#deletePrinter) | **DELETE** /v1/printers/{printerId} | Delete a printer and its captured jobs |
| [**getJob**](SimulatorApi.md#getJob) | **GET** /v1/printers/{printerId}/jobs/{jobId} | Get one job including its raw ZPL |
| [**getJobLabel**](SimulatorApi.md#getJobLabel) | **GET** /v1/printers/{printerId}/jobs/{jobId}/labels/{index}.png | Get one rendered label as a PNG |
| [**getPrinter**](SimulatorApi.md#getPrinter) | **GET** /v1/printers/{printerId} | Get a printer with live state |
| [**listJobs**](SimulatorApi.md#listJobs) | **GET** /v1/printers/{printerId}/jobs | List captured jobs, newest first |
| [**listPrinters**](SimulatorApi.md#listPrinters) | **GET** /v1/printers | List your printers |
| [**resetPrinter**](SimulatorApi.md#resetPrinter) | **POST** /v1/printers/{printerId}/reset | Clear all faults and flush held jobs |
| [**setPrinterFaults**](SimulatorApi.md#setPrinterFaults) | **POST** /v1/printers/{printerId}/faults | Inject or clear fault conditions |
| [**updatePrinter**](SimulatorApi.md#updatePrinter) | **PATCH** /v1/printers/{printerId} | Rename a printer or set its webhook URL |


<a id="clearJobs"></a>
# **clearJobs**
> clearJobs(printerId)

Delete all captured jobs

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    try {
      apiInstance.clearJobs(printerId);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#clearJobs");
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
| **printerId** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | No Content |  -  |
| **0** | Error |  -  |

<a id="createPrinter"></a>
# **createPrinter**
> PrinterBody createPrinter(createPrinterInputBody)

Create a virtual printer

Free tier: one ephemeral printer (24h idle TTL). Paid tiers: persistent printers. The ingest URL and webhook secret are only returned here.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $sim &#x3D; new StripyHorse\\Api\\SimulatorApi(null, $config); $printer &#x3D; $sim-&gt;createPrinter(new StripyHorse\\Model\\CreatePrinterInputBody([     &#39;name&#39; &#x3D;&gt; &#39;ci-run-42&#39;, &#39;preset&#39; &#x3D;&gt; &#39;4x6&#39;, ])); $addr &#x3D; $printer-&gt;getTcp()-&gt;getHost() . &#39;:&#39; . $printer-&gt;getTcp()-&gt;getPort(); // point the system under test at $addr, then assert with listJobs &#x60;&#x60;&#x60;  **curl**: &#x60;&#x60;&#x60;bash curl https://api.stripyhorse.io/v1/printers \\   -H \&quot;X-Api-Key: sh_live_YOUR_KEY\&quot; -H \&quot;Content-Type: application/json\&quot; \\   -d &#39;{\&quot;name\&quot;:\&quot;ci-run-42\&quot;,\&quot;preset\&quot;:\&quot;4x6\&quot;}&#39;  &#x60;&#x60;&#x60;

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    CreatePrinterInputBody createPrinterInputBody = new CreatePrinterInputBody(); // CreatePrinterInputBody | 
    try {
      PrinterBody result = apiInstance.createPrinter(createPrinterInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#createPrinter");
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
| **createPrinterInputBody** | [**CreatePrinterInputBody**](CreatePrinterInputBody.md)|  | |

### Return type

[**PrinterBody**](PrinterBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **0** | Error |  -  |

<a id="deletePrinter"></a>
# **deletePrinter**
> deletePrinter(printerId)

Delete a printer and its captured jobs

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    try {
      apiInstance.deletePrinter(printerId);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#deletePrinter");
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
| **printerId** | **String**|  | |

### Return type

null (empty response body)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | No Content |  -  |
| **0** | Error |  -  |

<a id="getJob"></a>
# **getJob**
> JobOutputBody getJob(printerId, jobId)

Get one job including its raw ZPL

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    Long jobId = 56L; // Long | 
    try {
      JobOutputBody result = apiInstance.getJob(printerId, jobId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#getJob");
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
| **printerId** | **String**|  | |
| **jobId** | **Long**|  | |

### Return type

[**JobOutputBody**](JobOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="getJobLabel"></a>
# **getJobLabel**
> String getJobLabel(printerId, jobId, index)

Get one rendered label as a PNG

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    Long jobId = 56L; // Long | 
    Long index = 56L; // Long | 
    try {
      String result = apiInstance.getJobLabel(printerId, jobId, index);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#getJobLabel");
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
| **printerId** | **String**|  | |
| **jobId** | **Long**|  | |
| **index** | **Long**|  | |

### Return type

**String**

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  * Content-Type -  <br>  |
| **0** | Error |  -  |

<a id="getPrinter"></a>
# **getPrinter**
> PrinterBody getPrinter(printerId)

Get a printer with live state

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    try {
      PrinterBody result = apiInstance.getPrinter(printerId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#getPrinter");
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
| **printerId** | **String**|  | |

### Return type

[**PrinterBody**](PrinterBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="listJobs"></a>
# **listJobs**
> ListJobsOutputBody listJobs(printerId, limit, before)

List captured jobs, newest first

For CI assertions and inbox views. Cursor-paged via before.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $jobs &#x3D; $sim-&gt;listJobs($printerId); assert(count($jobs-&gt;getJobs()) &#x3D;&#x3D;&#x3D; 1); assert($jobs-&gt;getJobs()[0]-&gt;getStatus() &#x3D;&#x3D;&#x3D; &#39;rendered&#39;); &#x60;&#x60;&#x60;  **curl**: &#x60;&#x60;&#x60;bash curl https://api.stripyhorse.io/v1/printers/$PRINTER_ID/jobs \\   -H \&quot;X-Api-Key: sh_live_YOUR_KEY\&quot; &#x60;&#x60;&#x60;

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    Long limit = 50L; // Long | 
    Long before = 56L; // Long | Return jobs with id lower than this cursor
    try {
      ListJobsOutputBody result = apiInstance.listJobs(printerId, limit, before);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#listJobs");
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
| **printerId** | **String**|  | |
| **limit** | **Long**|  | [optional] [default to 50] |
| **before** | **Long**| Return jobs with id lower than this cursor | [optional] |

### Return type

[**ListJobsOutputBody**](ListJobsOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="listPrinters"></a>
# **listPrinters**
> ListPrintersOutputBody listPrinters()

List your printers

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    try {
      ListPrintersOutputBody result = apiInstance.listPrinters();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#listPrinters");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**ListPrintersOutputBody**](ListPrintersOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="resetPrinter"></a>
# **resetPrinter**
> StateOutputBody resetPrinter(printerId)

Clear all faults and flush held jobs

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    try {
      StateOutputBody result = apiInstance.resetPrinter(printerId);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#resetPrinter");
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
| **printerId** | **String**|  | |

### Return type

[**StateOutputBody**](StateOutputBody.md)

### Authorization

[headerKey](../README.md#headerKey), [bearerKey](../README.md#bearerKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, application/problem+json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OK |  -  |
| **0** | Error |  -  |

<a id="setPrinterFaults"></a>
# **setPrinterFaults**
> StateOutputBody setPrinterFaults(printerId, faults)

Inject or clear fault conditions

Blocking faults hold incoming jobs in the receive buffer; clearing them flushes the queue in order.  **PHP** (&#x60;composer require stripyhorse/stripyhorse-php&#x60;): &#x60;&#x60;&#x60;php $sim-&gt;setPrinterFaults($printerId, new StripyHorse\\Model\\Faults([&#39;paper_out&#39; &#x3D;&gt; true])); // print something - it holds. Clear to flush: $sim-&gt;setPrinterFaults($printerId, new StripyHorse\\Model\\Faults()); &#x60;&#x60;&#x60;  **curl**: &#x60;&#x60;&#x60;bash curl https://api.stripyhorse.io/v1/printers/$PRINTER_ID/faults \\   -H \&quot;X-Api-Key: sh_live_YOUR_KEY\&quot; -H \&quot;Content-Type: application/json\&quot; \\   -d &#39;{\&quot;paperOut\&quot;:true}&#39;  &#x60;&#x60;&#x60;

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    Faults faults = new Faults(); // Faults | 
    try {
      StateOutputBody result = apiInstance.setPrinterFaults(printerId, faults);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#setPrinterFaults");
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
| **printerId** | **String**|  | |
| **faults** | [**Faults**](Faults.md)|  | |

### Return type

[**StateOutputBody**](StateOutputBody.md)

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

<a id="updatePrinter"></a>
# **updatePrinter**
> PrinterBody updatePrinter(printerId, updatePrinterInputBody)

Rename a printer or set its webhook URL

### Example
```java
// Import classes:
import io.stripyhorse.ApiClient;
import io.stripyhorse.ApiException;
import io.stripyhorse.Configuration;
import io.stripyhorse.auth.*;
import io.stripyhorse.models.*;
import io.stripyhorse.api.SimulatorApi;

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

    SimulatorApi apiInstance = new SimulatorApi(defaultClient);
    String printerId = "printerId_example"; // String | 
    UpdatePrinterInputBody updatePrinterInputBody = new UpdatePrinterInputBody(); // UpdatePrinterInputBody | 
    try {
      PrinterBody result = apiInstance.updatePrinter(printerId, updatePrinterInputBody);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SimulatorApi#updatePrinter");
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
| **printerId** | **String**|  | |
| **updatePrinterInputBody** | [**UpdatePrinterInputBody**](UpdatePrinterInputBody.md)|  | |

### Return type

[**PrinterBody**](PrinterBody.md)

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

