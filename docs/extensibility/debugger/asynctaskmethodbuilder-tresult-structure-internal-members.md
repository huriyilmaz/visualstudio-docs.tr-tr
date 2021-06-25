---
description: Bu konuda System.Runtime.CompilerServices.AsyncTaskMethodBuilder sınıfının iç üyeleri açıklanmıştır.
title: AsyncTaskMethodBuilder &lt; TResult &gt; Yapısı - İç Üyeler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca9d5ccfcd5870902cc40a623aabb93a3115f469
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903807"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; yapısı - iç üyeler
Bu konuda sınıfının iç üyeleri <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> açıklanmıştır. Bu sınıf hakkında genel bilgi için başvuru <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> konu başlığına bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Derleme:** mscorlib (mscorlib.dll)

 Bu iç üyelere .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Dahili üyeler

|Ad|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Hata ayıklayıcısına bu oluşturucusu benzersiz olarak tanımlamak için kullanılmaktadır bir nesnesi alır.|
|[m_task alanı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Yavaş başlatılan yerleşik görevi temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework için paralel uzantı iç .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
