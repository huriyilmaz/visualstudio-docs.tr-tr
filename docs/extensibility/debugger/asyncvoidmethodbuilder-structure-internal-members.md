---
description: Bu konu, System. Runtime. CompilerServices. AsyncVoidMethodBuilder sınıfının iç üyelerini açıklar.
title: AsyncVoidMethodBuilder yapısı-Iç Üyeler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad209fb94a9857fe0596f1e25b0dec844d03ca8f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151150"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder yapısı-dahili Üyeler
Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)

 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>İç Üyeler

|Ad|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Bu oluşturucuyu hata ayıklayıcıya benzersiz bir şekilde tanımlamak için kullanılabilecek bir nesne alır.|
|[m_objectIdForDebugger alanı](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Bu oluşturucuyu benzersiz bir şekilde tanımlamak için hata ayıklayıcı tarafından kullanılan geç Initialized nesnesini temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET Framework için paralel uzantı iç işlevleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
