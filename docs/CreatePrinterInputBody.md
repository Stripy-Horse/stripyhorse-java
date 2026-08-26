

# CreatePrinterInputBody


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**anonymize** | **Boolean** | Mask PII and strip graphics from every captured frame |  [optional] |
|**dpmm** | [**DpmmEnum**](#DpmmEnum) | Print density in dots/mm (152/203/300/600 dpi); default 8 |  [optional] |
|**heightMm** | **Double** |  |  [optional] |
|**mode** | [**ModeEnum**](#ModeEnum) |  |  [optional] |
|**name** | **String** |  |  |
|**preset** | [**PresetEnum**](#PresetEnum) | Named label size in inches; alternative to widthMm/heightMm |  [optional] |
|**webhookUrl** | **String** |  |  [optional] |
|**widthMm** | **Double** |  |  [optional] |



## Enum: DpmmEnum

| Name | Value |
|---- | -----|
| NUMBER_6 | 6l |
| NUMBER_8 | 8l |
| NUMBER_12 | 12l |
| NUMBER_24 | 24l |



## Enum: ModeEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| EPHEMERAL | &quot;ephemeral&quot; |
| PERSISTENT | &quot;persistent&quot; |



## Enum: PresetEnum

| Name | Value |
|---- | -----|
| _4X6 | &quot;4x6&quot; |
| _6X4 | &quot;6x4&quot; |
| _4X4 | &quot;4x4&quot; |
| _4X2 | &quot;4x2&quot; |
| _2X4 | &quot;2x4&quot; |
| _3X5 | &quot;3x5&quot; |
| _5X3 | &quot;5x3&quot; |
| _2X3 | &quot;2x3&quot; |
| _3X2 | &quot;3x2&quot; |
| NETSTAMP | &quot;netstamp&quot; |
| _2_25X1_25 | &quot;2.25x1.25&quot; |
| _2X1 | &quot;2x1&quot; |
| _3X1 | &quot;3x1&quot; |
| _4X1 | &quot;4x1&quot; |
| _1X1 | &quot;1x1&quot; |
| _4X3 | &quot;4x3&quot; |
| _4X8 | &quot;4x8&quot; |
| A6 | &quot;a6&quot; |



