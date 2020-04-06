---
title: AsyncVoidMethodBuilder Yapısı - Dahili Üyeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739292"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder yapısı - dahili üyeler
Bu konu <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> için başvuru konusuna bakın.

 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Montaj:** mscorlib (mscorlib.dll olarak)

 Bu dahili üyelere .NET Framework'den erişemediğiniz için, ortak ara dilde (CIL) aşağıdaki sözdizimi sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Dahili üyeler

|Adı|Açıklama|
|----------|-----------------|
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Hata ayıklayan için bu oluşturucuyu benzersiz olarak tanımlamak için kullanılabilecek bir nesne alır.|
|[m_objectIdForDebugger alanı](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Hata ayıklama nın bu oluşturucuyu benzersiz olarak tanımlamak için kullandığı lazily initialized nesneyi temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET Framework için paralel uzantı dahili](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
