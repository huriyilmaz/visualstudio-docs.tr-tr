---
title: IDebugProcessEx2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723335"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) bağlı olduğu veya işlemden ayırdığı bir işlemi bildirmesine olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi bu arabirimi Aşağıdakiler için [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimiyle aynı nesne üzerinde uygular:

- Bir işleme bağlı oturumların destek takibi

- Birden çok hata ayıklama motoru arasında otomatik eklemeyi destekleyin

  Özel bağlantı noktası tedarikçisi isterse bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar

- SDM, bu arabirimi `IDebugProcess2` elde etmek için [QueryInterface'i](/cpp/atl/queryinterface) bir arabirimde çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugProcessEx2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[İliştir](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|İşlemi, bir oturumun artık işlemi hata ayıklama olarak bildirdiğini bildirir.|
|[Ayır](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|İşlemi, bir oturumun artık işlemi hata ayıklamadığını bildirir.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Hata ayıklama motorlarının listesi için program düğümleri ekler.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim SDM ve işlem arasında özeldir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portpriv.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
