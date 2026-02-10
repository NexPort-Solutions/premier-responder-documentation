# Action Type: Set_Control_Value

Action ID: **35**

## When to use

Use when clicking a hyperlink should populate a narrative control from another source.

## Fields In Action Editor

- **Control ID:** Enter the target control ID to set.
- **From:** Choose the source type (question, property, action, narrative, control).
- **Source (changes by From selection):** Select or enter the source value for the selected From type.

## What The Call-Taker Sees

The target control is updated from the source. For some control types this can trigger the same behavior as user interaction (for example button/hyperlink click when text matches).

## Example Setup

- Control ID: cboPatientCondition
- From: question
- Source Question: Primary Condition

## Related

* [Hyperlinks Overview](README.md)
* [Guide Card Editor](<../Guide Card Editor.md>)

