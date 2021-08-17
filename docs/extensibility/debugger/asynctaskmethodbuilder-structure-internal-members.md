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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 451696422e43cb257beb879980206b6c97f022743cf5ffd28eb40938d331460c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434691"
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
