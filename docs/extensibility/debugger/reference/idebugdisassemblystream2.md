---
description: Bu arabirim bir yönergelerin akışını temsil eder.
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e42d8019c854ca800dd35028fe82a158bc3a428e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119522"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Bu arabirim bir yönergelerin akışını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı, program kodunun ayrımlarını desteklemek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetDisassemblyStream yöntemine yapılan bir çağrı](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugDisassemblyStream2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Ayrık akışta geçerli konumdan başlayarak yönergeleri okur.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Disassembly akışında belirtilen konuma göre belirli sayıdaki yönergelerin okuma işaretçisini taşır.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Belirli bir kod bağlamı için kod konumu tanımlayıcısı döndürür.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Belirtilen kod konumu tanımlayıcısına karşılık gelen bir kod bağlamı nesnesi döndürür.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Geçerli kod konumunu temsil eden bir kod konumu tanımlayıcısı döndürür.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Bu ayrık akışla ilişkili kaynak belgeyi alır.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Bu ayrık akışın kapsamını alır.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Bu ayrık akışın boyutunu alır.|

## <a name="remarks"></a>Açıklamalar
 Adres alanı tamamını veya yalnızca alan içindeki bir işlevi veya modülü temsil etmek için ayrım akışı oluşturulabilir. Her yönerge Read yöntemine yapılan bir çağrı tarafından döndürülen [bir DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) [yapısıyla temsil](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) edilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
