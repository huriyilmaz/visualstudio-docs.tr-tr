---
description: Bu konu, System. Runtime. CompilerServices. AsyncTaskMethodBuilder sınıfının iç üyelerini açıklar.
title: AsyncTaskMethodBuilder &lt; TResult &gt; yapısı-iç Üyeler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35e1ca4d19727383bdd7c957bc59fd6b6568c9f5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145657"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; yapısı-iç Üyeler
Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>İç Üyeler

|Ad|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Bu oluşturucuyu hata ayıklayıcıya benzersiz bir şekilde tanımlamak için kullanılabilecek bir nesne alır.|
|[m_task alanı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Geç tarafından başlatılan oluşturulmuş görevi temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework için paralel uzantı iç işlevleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
