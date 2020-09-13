---
title: AsyncTaskMethodBuilder Yapısı - Dahili Üyeler
titleSuffix: ''
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f79ee4c717774ef61fc0aa07fe7ecf2c5c216c04
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036892"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder yapısı-dahili Üyeler
Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

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
