---
title: AsyncTaskMethodBuilder Yapısı - Dahili Üyeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739380"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder yapısı - dahili üyeler
Bu konu <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> için başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montaj:** mscorlib (mscorlib.dll olarak)

 Bu dahili üyelere .NET Framework'den erişemediğiniz için, ortak ara dilde (CIL) aşağıdaki sözdizimi sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Dahili üyeler

|Adı|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Hata ayıklayan için bu oluşturucuyu benzersiz olarak tanımlamak için kullanılabilecek bir nesne alır.|
|[m_builder alanı](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Bu genel olmayan örnek temsilcilerinin bulunduğu genel oluşturucu nesneyi temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [.NET Framework için paralel uzantı dahili](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
