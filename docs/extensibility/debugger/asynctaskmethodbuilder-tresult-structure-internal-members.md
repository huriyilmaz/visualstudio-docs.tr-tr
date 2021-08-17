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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7864f45aaed3d16784a451ce5a0161218650246806da3debce2ef8ea1d3ab4e0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434690"
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
- [Ağ için paralel uzantı iç .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
