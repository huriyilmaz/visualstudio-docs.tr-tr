---
description: Bu arabirim, üzerinde çalıştığı bağlantı noktasıyla ayıklanabilecek bir programı kaydeder veya kaydını siler.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4000426b72472d57b589f26543dd1547f8dc982
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072396"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Bu arabirim, üzerinde çalıştığı bağlantı noktasıyla ayıklanabilecek bir programı kaydeder veya kaydını siler.

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi, bağlantı noktasından program eklemeyi ve kaldırmayı desteklemek için uygular. Genellikle [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimini uygulayan aynı nesneye uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Arabirimdeki bir [QueryInterface](/cpp/atl/queryinterface) çağrısı `IDebugPort2` Bu arabirimi döndürür. Ayrıca, [Getportnotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) çağrısı bu arabirimi döndürür. Bir hata ayıklama altyapısı, bu arabirimi [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)için bir parametre olarak görebilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPortNotify2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Üzerinde çalıştığı bağlantı noktasıyla ayıklanabilecek bir programı kaydeder.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Üzerinde çalıştığı bağlantı noktasından hata ayıklaabilecek bir programın kaydını siler.|

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama bağlantı noktasının, programların ne zaman yüklendiğini veya bellekten yüklenmediğini bilen bir yolu yoksa, özel bir bağlantı noktası tedarikçinin bu arabirimi uygulaması gerekir. Belirli bir bağlantı noktası aracılığıyla hata ayıklama için yüklenen tüm programlar bu arabirim kullanılarak izlenir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
