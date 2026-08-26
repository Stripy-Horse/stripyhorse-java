

# PrinterBody


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**anonymize** | **Boolean** | When true, PII is masked and graphics stripped from every captured frame |  |
|**createdAt** | **OffsetDateTime** |  |  |
|**dpmm** | **Long** |  |  |
|**expiresAt** | **OffsetDateTime** |  |  [optional] |
|**heightMm** | **Double** |  |  |
|**id** | **String** |  |  |
|**ingestUrl** | **String** | HTTPS print capability URL. Only returned on creation. |  [optional] |
|**mode** | [**ModeEnum**](#ModeEnum) |  |  |
|**name** | **String** |  |  |
|**state** | [**StatusSnapshot**](StatusSnapshot.md) |  |  [optional] |
|**tcp** | [**PrinterBodyTCPStruct**](PrinterBodyTCPStruct.md) |  |  |
|**webhookSecret** | **String** | HMAC-SHA256 key for X-Stripy-Horse-Signature. Only returned on creation. |  [optional] |
|**webhookUrl** | **String** |  |  [optional] |
|**widthMm** | **Double** |  |  |



## Enum: ModeEnum

| Name | Value |
|---- | -----|
| EPHEMERAL | &quot;ephemeral&quot; |
| PERSISTENT | &quot;persistent&quot; |



