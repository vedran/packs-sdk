---
nav: "ProgressBarSchema"
note: "This file is autogenerated from TypeScript definitions. Make edits to the comments in the TypeScript file and then run `make docs` to regenerate this file."
search:
  boost: 0.1
---
# Interface: ProgressBarSchema

[core](../modules/core.md).ProgressBarSchema

A schema representing a return value or object property that is a number that should
be rendered as a progress bar.

## Hierarchy

- `BaseNumberSchema`<[`ProgressBar`](../enums/core.ValueHintType.md#progressbar)\>

  ↳ **`ProgressBarSchema`**

## Properties

### codaType

• **codaType**: [`ProgressBar`](../enums/core.ValueHintType.md#progressbar)

Instructs Coda to render this value as a progress bar.

#### Overrides

BaseNumberSchema.codaType

___

### description

• `Optional` **description**: `string`

A explanation of this object schema property shown to the user in the UI.

If your pack has an object schema with many properties, it may be useful to
explain the purpose or contents of any property that is not self-evident.

#### Inherited from

BaseNumberSchema.description

___

### maximum

• `Optional` **maximum**: `string` \| `number`

The maximum value selectable by this progress bar.

___

### minimum

• `Optional` **minimum**: `string` \| `number`

The minimum value selectable by this progress bar.

___

### showValue

• `Optional` **showValue**: `boolean`

Whether to display the underlying numeric value in addition to the progress bar.

___

### step

• `Optional` **step**: `string` \| `number`

The minimum amount the progress bar can be moved when dragged.

___

### type

• **type**: [`Number`](../enums/core.ValueType.md#number)

Identifies this schema as relating to a number value.

#### Inherited from

BaseNumberSchema.type
