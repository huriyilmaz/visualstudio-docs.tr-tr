---
description: Bu makalede System. Runtime. CompilerServices. AsyncTaskMethodBuilder sınıfının iç üyeleri açıklanmaktadır.
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
ms.openlocfilehash: fb9897fd4a15b78a6130d68ddcaf3c1089def8ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133295"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder yapısı-dahili Üyeler
Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 bu iç üyelere .NET Framework erişemediği için, ortak ara dil (cıl) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>İç Üyeler

|Ad|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Bu oluşturucuyu hata ayıklayıcıya benzersiz bir şekilde tanımlamak için kullanılabilecek bir nesne alır.|
|[m_builder alanı](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Bu genel olmayan örneğin temsilcilerin bulunduğu genel Oluşturucu nesnesini temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [.NET Framework için paralel uzantı iç işlevleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
