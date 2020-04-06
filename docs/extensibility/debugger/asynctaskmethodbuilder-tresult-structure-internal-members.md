---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Yapısı - Dahili Üyeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739338"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; yapısı - dahili üyeler
Bu konu <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> için başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montaj:** mscorlib (mscorlib.dll olarak)

 Bu dahili üyelere .NET Framework'den erişemediğiniz için, ortak ara dilde (CIL) aşağıdaki sözdizimi sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Dahili üyeler

|Adı|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Hata ayıklayan için bu oluşturucuyu benzersiz olarak tanımlamak için kullanılabilecek bir nesne alır.|
|[m_task alanı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Lazily başharfle fünyeli oluşturulmuş görevi temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework için paralel uzantı dahili](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
