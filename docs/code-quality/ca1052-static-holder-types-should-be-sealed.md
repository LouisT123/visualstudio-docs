---
title: "CA1052: Static holder types should be Static or NotInheritable"
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords:
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CPP
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1052: Static holder types should be Static or NotInheritable

|||
|-|-|
|TypeName|StaticHolderTypesAnalyzer|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Breaking Change|Breaking|

## Cause

A non-abstract type contains only static members (other than a possible default constructor) and is not declared with the [static](/dotnet/csharp/language-reference/keywords/static) or [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) modifier.

By default, this rule only looks at externally visible types, but this is [configurable](#configurability).

## Rule description

Rule CA1052 assumes that a type that contains only static members is not designed to be inherited, because the type does not provide any functionality that can be overridden in a derived type. A type that is not meant to be inherited should be marked with the `static` modifier in C# to prohibit its use as a base type. Additionally, its default constructor should be removed. In Visual Basic, the class should be converted to a [module](/dotnet/visual-basic/language-reference/statements/module-statement).

This rule does not fire for abstract classes or classes that have a base class. However, the rule does fire for classes that support an empty interface.

> [!NOTE]
> In the FxCop analyzer implementation of this rule, it also encompasses the functionality of [rule CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md).

## How to fix violations

To fix a violation of this rule, mark the type as `static` and remove the default constructor (C#), or convert it to a module (Visual Basic).

## When to suppress warnings

Suppress a warning from this rule only if the type is designed to be inherited. The absence of the `static` modifier suggests that the type is useful as a base type.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not through static code analysis), you can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an EditorConfig file in your project:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Design). For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).

## Example of a violation

The following example shows a type that violates the rule:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## Fix with the static modifier

The following example shows how to fix a violation of this rule by marking the type with the `static` modifier in C#:

```csharp
public static class StaticMembers
{
    public static int SomeProperty { get; set; }
    public static void SomeMethod() { }
}
```