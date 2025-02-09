---
title: "CA1032: Implement standard exception constructors"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords:
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1032: Implement standard exception constructors

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Breaking Change|Non-breaking|

## Cause

A type extends <xref:System.Exception?displayProperty=fullName> but doesn't declare all the required constructors.

## Rule description

Exception types must implement the following three constructors:

- public NewException()

- public NewException(string)

- public NewException(string, Exception)

Additionally, if you're running legacy FxCop static code analysis as opposed to [Roslyn-based FxCop analyzers](../code-quality/roslyn-analyzers-overview.md), the absence of a fourth constructor also generates a violation:

- protected or private NewException(SerializationInfo, StreamingContext)

Failure to provide the full set of constructors can make it difficult to correctly handle exceptions. For example, the constructor that has the signature `NewException(string, Exception)` is used to create exceptions that are caused by other exceptions. Without this constructor, you can't create and throw an instance of your custom exception that contains an inner (nested) exception, which is what managed code should do in such a situation.

The first three exception constructors are public by convention. The fourth constructor is protected in unsealed classes, and private in sealed classes. For more information, see [CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md).

## How to fix violations

To fix a violation of this rule, add the missing constructors to the exception, and make sure that they have the correct accessibility.

## When to suppress warnings

It's safe to suppress a warning from this rule when the violation is caused by using a different access level for the public constructors. Additionally, it's okay to suppress the warning for the `NewException(SerializationInfo, StreamingContext)` constructor if you're building a Portable Class Library (PCL).

## Example

The following example contains an exception type that violates this rule and an exception type that is correctly implemented.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## See also

[CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md)