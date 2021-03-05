---
description: Bir bağlantı noktası sağlayıcısı için yerel ayar desteği sağlar.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c29bd3fb882be6529daa0d26ab4cde23c11d0bc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167067"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Bir bağlantı noktası sağlayıcısı için yerel ayar desteği sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı bu arabirimi yerel ayarı ayarlamak için uygular.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda **IDebugPortSupplierLocale2** yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Bağlantı noktası sağlayıcısı için yerel ayarı ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
