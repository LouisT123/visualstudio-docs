---
title: "CA1814: Prefer jagged arrays over multidimensional"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords:
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1814: Prefer jagged arrays over multidimensional

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft.Performance|
|Breaking Change|Breaking|

## Cause
A member is declared as a multidimensional array.

## Rule description
A jagged array is an array whose elements are arrays. The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data.

## How to fix violations
To fix a violation of this rule, change the multidimensional array to a jagged array.

## When to suppress warnings
Suppress a warning from this rule if the multidimensional array does not waste space.

## Example
The following example shows declarations for jagged and multidimensional arrays.

[!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
[!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]