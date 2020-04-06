---
title: IDebugPortSupplierEx2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26387618b320ed56ce754e64698fbb1c4223f2f6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724316"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Bir bağlantı noktası tedarikçisinin bir çekirdek sunucu seçmek ve onlarla etkileşimde bulunur.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, kullanılacak çekirdek sunucuyu seçebilmek için bu arabirimi uygular.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda **IDebugPortSupplierEx2**yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Bağlantı noktası tedarikçisi için çekirdek sunucuyu ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portpriv.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
