---
description: Bu arabirim bir yönerge akışını temsil eder.
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 760d77ced3cc07da2dd02c21cf3ed0200df14231
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166573"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Bu arabirim bir yönerge akışını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir hata ayıklama altyapısı, bir programın kodunun ayrıştırılmış derlemesini desteklemek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) yöntemine yapılan bir çağrı bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDisassemblyStream2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Okuyamaz](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Ayrıştırılmış birleştirme akışındaki geçerli konumdan başlayan yönergeleri okur.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Ayırma akışındaki okuma işaretçisini, belirtilen bir konuma göre verilen sayıda yönergeye kaydırır.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Belirli bir kod bağlamı için bir kod konum tanımlayıcısı döndürür.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Belirtilen kod konumu tanımlayıcısına karşılık gelen bir kod bağlamı nesnesi döndürür.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Geçerli kod konumunu temsil eden bir kod konum tanımlayıcısı döndürür.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Bu ayırt derleme akışıyla ilişkili kaynak belgeyi alır.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Bu ayırt derleme akışının kapsamını alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Bu ayırt derleme akışının boyutunu alır.|

## <a name="remarks"></a>Açıklamalar
 Tek derleme akışı, tüm adres alanını veya boşluk içindeki bir işlevi ya da modülü göstermek için oluşturulabilir. Her yönerge [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) yöntemine yapılan bir çağrı tarafından döndürülen bir [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısıyla temsil edilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
