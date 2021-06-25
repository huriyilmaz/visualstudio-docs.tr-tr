---
description: Bu makalede System.Runtime.CompilerServices.AsyncTaskMethodBuilder sınıfının iç üyeleri açıklanmıştır.
title: AsyncTaskMethodBuilder Yapısı - Dahili Üyeler
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b21045688fc2be555c7a42d6e3b9014b66c761
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903846"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder yapısı - iç üyeler
Bu konuda sınıfının iç üyeleri <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> açıklanmıştır. Bu sınıf hakkında genel bilgi için başvuru <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> konu başlığına bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Derleme:** mscorlib (mscorlib.dll)

 Bu iç üyelere .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Dahili üyeler

|Ad|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Hata ayıklayıcısına bu oluşturucusu benzersiz olarak tanımlamak için kullanılmaktadır bir nesnesi alır.|
|[m_builder alanı](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Bu genel olmayan örneğin temsilci olarak temsil ettiği genel oluşturucu nesnesini temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [.NET Framework için paralel uzantı iç .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
