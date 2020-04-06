---
title: IDebugPortNotify2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724923"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Bu arabirim, üzerinde çalışan bağlantı noktasıyla hata ayıklanabilecek bir programı kaydeder veya kaydeder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, bağlantı noktasından program eklemeyi ve kaldırmayı desteklemek için bu arabirimi uygular. Genellikle [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimini uygulayan aynı nesne üzerinde uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Arabirimdeki `IDebugPort2` [QueryInterface'e](/cpp/atl/queryinterface) yapılan bir çağrı bu arabirimi döndürür. Ayrıca, [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) için bir çağrı bu arabirimi döndürür. Hata ayıklama altyapısı bu arabirimi [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)için bir parametre olarak görebilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPortNotify2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Üzerinde çalışan bağlantı noktası ile debugged olabilir bir program kaydeder.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Üzerinde çalışan bağlantı noktasından çıkarılabilir bir program kaydını boşaltır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama bağlantı noktası, programların ne zaman yüklendiğini veya boşaltıldığında niçin bir yol yoksa, özel bir bağlantı noktası tedarikçisinin bu arabirimi uygulaması gerekir. Belirli bir bağlantı noktası üzerinden hata ayıklama için yüklenen tüm programlar bu arabirim kullanılarak izlenir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
