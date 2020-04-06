---
title: IDebugDisassemblyStream2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732039"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Bu arabirim bir yönerge akışını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, bir programın kodunun devre dolmasını desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) yöntemine yapılan bir çağrı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugDisassemblyStream2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Sökme akışındaki geçerli konumdan başlayarak yönergeleri okur.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Okuma işaretçisini sökme akışındaki okundu işaretçisini belirli bir konuma göre belirli sayıda yönerge taşır.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Belirli bir kod bağlamı için kod konum tanımlayıcısı döndürür.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Belirtilen kod konum tanımlayıcısına karşılık gelen bir kod bağlamı nesnesi döndürür.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Geçerli kod konumunu temsil eden bir kod konum tanımlayıcısı verir.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Bu sökme akışıyla ilişkili kaynak belgeyi alır.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Bu sökme akışının kapsamını alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Bu sökme akışının boyutunu alır.|

## <a name="remarks"></a>Açıklamalar
 Sökme akışı, tüm adres alanını veya boşluk içindeki bir işlevi veya modülü temsil etmek için oluşturulabilir. Her yönerge, [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine yapılan bir çağrıyla döndürülen bir [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısıyla temsil edilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
