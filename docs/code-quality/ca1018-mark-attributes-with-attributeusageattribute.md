---
title: "CA1018: Mark attributes with AttributeUsageAttribute"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords:
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1018: Mark attributes with AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Breaking Change|Breaking|

## Cause
The <xref:System.AttributeUsageAttribute?displayProperty=fullName> attribute is not present on the custom attribute.

## Rule description
When you define a custom attribute, mark it by using <xref:System.AttributeUsageAttribute> to indicate where in the source code the custom attribute can be applied. The meaning and intended usage of an attribute will determine its valid locations in code. For example, you might define an attribute that identifies the person who is responsible for maintaining and enhancing each type in a library, and that responsibility is always assigned at the type level. In this case, compilers should enable the attribute on classes, enumerations, and interfaces, but should not enable it on methods, events, or properties. Organizational policies and procedures would dictate whether the attribute should be enabled on assemblies.

The <xref:System.AttributeTargets?displayProperty=fullName> enumeration defines the targets that you can specify for a custom attribute. If you omit <xref:System.AttributeUsageAttribute>, your custom attribute will be valid for all targets, as defined by the `All` value of <xref:System.AttributeTargets> enumeration.

## How to fix violations
To fix a violation of this rule, specify targets for the attribute by using <xref:System.AttributeUsageAttribute>. See the following example.

## When to suppress warnings
You should fix a violation of this rule instead of excluding the message. Even if the attribute inherits <xref:System.AttributeUsageAttribute>, the attribute should be present to simplify code maintenance.

## Example
The following example defines two attributes. `BadCodeMaintainerAttribute` incorrectly omits the <xref:System.AttributeUsageAttribute> statement, and `GoodCodeMaintainerAttribute` correctly implements the attribute that is described earlier in this section. Note that the property `DeveloperName` is required by the design rule [CA1019: Define accessors for attribute arguments](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) and is included for completeness.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## Related rules
[CA1019: Define accessors for attribute arguments](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: Avoid unsealed attributes](../code-quality/ca1813-avoid-unsealed-attributes.md)

## See also

- [Attributes](/dotnet/standard/design-guidelines/attributes)