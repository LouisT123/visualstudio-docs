---
title: "CA1823: Avoid unused private fields"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords:
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1823: Avoid unused private fields

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Breaking Change|Non-breaking|

## Cause
This rule is reported when a private field in your code exists but is not used by any code path.

## Rule description
Private fields were detected that do not appear to be accessed in the assembly.

## How to fix violations
To fix a violation of this rule, remove the field or add code that uses it.

## When to suppress warnings
It is safe to suppress a warning from this rule.

## Related rules
[CA1812: Avoid uninstantiated internal classes](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Review unused parameters](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Remove unused locals](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Avoid uncalled private code](../code-quality/ca1811-avoid-uncalled-private-code.md)