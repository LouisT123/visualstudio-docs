---
title: "CA1308: Normalize strings to uppercase"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords:
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1308: Normalize strings to uppercase

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft.Globalization|
|Breaking Change|Non-breaking|

## Cause
An operation normalizes a string to lowercase.

## Rule description
Strings should be normalized to uppercase. A small group of characters, when they are converted to lowercase, cannot make a round trip. To make a round trip means to convert the characters from one locale to another locale that represents character data differently, and then to accurately retrieve the original characters from the converted characters.

## How to fix violations
Change operations that convert strings to lowercase so that the strings are converted to uppercase instead. For example, change `String.ToLower(CultureInfo.InvariantCulture)` to `String.ToUpper(CultureInfo.InvariantCulture)`.

## When to suppress warnings
It is safe to suppress a warning message when you are not making security decision based on the result (for example, when you are displaying it in the UI).

## See also
[Globalization Warnings](../code-quality/globalization-warnings.md)