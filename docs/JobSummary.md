

# JobSummary


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**error** | **String** |  |  [optional] |
|**id** | **Long** |  |  |
|**labelCount** | **Long** |  |  |
|**receivedAt** | **OffsetDateTime** |  |  |
|**source** | [**SourceEnum**](#SourceEnum) |  |  |
|**status** | [**StatusEnum**](#StatusEnum) |  |  |
|**zplBytes** | **Long** |  |  |



## Enum: SourceEnum

| Name | Value |
|---- | -----|
| TCP | &quot;tcp&quot; |
| HTTPS | &quot;https&quot; |



## Enum: StatusEnum

| Name | Value |
|---- | -----|
| RENDERED | &quot;rendered&quot; |
| RENDER_FAILED | &quot;render_failed&quot; |



