

# Element


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**align** | [**AlignEnum**](#AlignEnum) | Alignment when wrapping |  [optional] |
|**anchor** | [**AnchorEnum**](#AnchorEnum) | Which corner x,y names. topLeft (^FO, default); bottomLeft (^FT: the text baseline, what most designer-exported ZPL uses); the Right variants make x the field&#39;s right edge (ZPL justification 1) |  [optional] |
|**columns** | **Long** | Grid columns (default 1) |  [optional] |
|**cornerRadius** | **Long** | Box corner rounding 0-8 |  [optional] |
|**data** | **String** | Barcode payload; {{name}} interpolates |  [optional] |
|**diameter** | **Long** | Circle diameter in dots |  [optional] |
|**errorCorrection** | [**ErrorCorrectionEnum**](#ErrorCorrectionEnum) | QR error correction (default M) |  [optional] |
|**font** | **String** | Printer font: 0 (scalable, default) or A-Z |  [optional] |
|**fontHeight** | **Long** | Character height in dots (text) |  [optional] |
|**fontWidth** | **Long** | Character width in dots; 0 follows fontHeight |  [optional] |
|**height** | **Long** | Bar height in dots (1D) / box height in dots (box) |  [optional] |
|**length** | **Long** | Line length in dots |  [optional] |
|**lineSpacing** | **Long** | Extra dots between wrapped lines |  [optional] |
|**lines** | **Long** | Max lines when wrapping (default 1) |  [optional] |
|**magnification** | **Long** | QR module magnification (default 3) |  [optional] |
|**maxWidth** | **Long** | Wrap text into a block this many dots wide |  [optional] |
|**mode** | [**ModeEnum**](#ModeEnum) | Code 128 mode: N none (default), U UCC case, A automatic subset switching, D UCC/EAN application identifiers |  [optional] |
|**moduleSize** | **Long** | DataMatrix module size in dots (default 4) |  [optional] |
|**moduleWidth** | **Long** | Narrow element width in dots (1D; default 3) |  [optional] |
|**orientation** | [**OrientationEnum**](#OrientationEnum) | Line direction |  [optional] |
|**png** | **String** | PNG/GIF/JPEG, base64-encoded |  [optional] |
|**printText** | **Boolean** | Print the human-readable line under 1D barcodes (default true) |  [optional] |
|**rotation** | [**RotationEnum**](#RotationEnum) |  |  [optional] |
|**rows** | **Long** | Grid rows (default 1) |  [optional] |
|**text** | **String** | Text content; {{name}} interpolates from variables |  [optional] |
|**thickness** | **Long** | Stroke thickness in dots (default 1) |  [optional] |
|**threshold** | **Long** | Bitonal threshold (default 128) |  [optional] |
|**type** | [**TypeEnum**](#TypeEnum) | What to place |  |
|**width** | **Long** | Box/image width in dots |  [optional] |
|**x** | **Long** | Left edge in dots |  [optional] |
|**y** | **Long** | Top edge in dots |  [optional] |
|**zpl** | **String** | Verbatim ZPL commands (raw only) - the escape hatch |  [optional] |



## Enum: AlignEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| LEFT | &quot;left&quot; |
| CENTER | &quot;center&quot; |
| RIGHT | &quot;right&quot; |
| JUSTIFY | &quot;justify&quot; |



## Enum: AnchorEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| TOP_LEFT | &quot;topLeft&quot; |
| BOTTOM_LEFT | &quot;bottomLeft&quot; |
| TOP_RIGHT | &quot;topRight&quot; |
| BOTTOM_RIGHT | &quot;bottomRight&quot; |



## Enum: ErrorCorrectionEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| L | &quot;L&quot; |
| M | &quot;M&quot; |
| Q | &quot;Q&quot; |
| H | &quot;H&quot; |



## Enum: ModeEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| N | &quot;N&quot; |
| U | &quot;U&quot; |
| A | &quot;A&quot; |
| D | &quot;D&quot; |



## Enum: OrientationEnum

| Name | Value |
|---- | -----|
| EMPTY | &quot;&quot; |
| H | &quot;h&quot; |
| V | &quot;v&quot; |



## Enum: RotationEnum

| Name | Value |
|---- | -----|
| NUMBER_0 | 0l |
| NUMBER_90 | 90l |
| NUMBER_180 | 180l |
| NUMBER_270 | 270l |



## Enum: TypeEnum

| Name | Value |
|---- | -----|
| TEXT | &quot;text&quot; |
| BARCODE128 | &quot;barcode128&quot; |
| BARCODE39 | &quot;barcode39&quot; |
| QR | &quot;qr&quot; |
| DATAMATRIX | &quot;datamatrix&quot; |
| BOX | &quot;box&quot; |
| LINE | &quot;line&quot; |
| CIRCLE | &quot;circle&quot; |
| GRID | &quot;grid&quot; |
| IMAGE | &quot;image&quot; |
| RAW | &quot;raw&quot; |



