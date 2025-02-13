---
title: "CA2142: Transparent code should not be protected with LinkDemands"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA2142: Transparent code should not be protected with LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Category|Microsoft.Security|
|Breaking Change|Breaking|

## Cause
A transparent method requires a <xref:System.Security.Permissions.SecurityAction> or other security demand.

## Rule description
This rule fires on transparent methods that require LinkDemands to access them. Security transparent code should not be responsible for verifying the security of an operation, and therefore should not demand permissions. Because transparent methods are supposed to be security neutral, they should not be making any security decisions. Additionally, safe critical code, which does make security decisions, should not be relying on transparent code to have previously made such a decision.

## How to fix violations
To fix a violation of this rule, remove the link demand on the transparent method or mark the method with <xref:System.Security.SecuritySafeCriticalAttribute> attribute if it is performing security checks, such as security demands.

## When to suppress warnings
Do not suppress a warning from this rule.

## Example
In the following example, the rule fires on the method because the method is transparent and is marked with a LinkDemand <xref:System.Security.PermissionSet> that contains an <xref:System.Security.Permissions.SecurityAction>.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Do not suppress a warning from this rule.