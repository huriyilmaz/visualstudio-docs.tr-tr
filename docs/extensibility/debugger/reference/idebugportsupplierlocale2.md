---
description: Bir bağlantı noktası tedarikçi için yerel bölge desteği sağlar.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fb273e38e207f36f7d438b7fba0bfe093f1c8344
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088022"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Bir bağlantı noktası tedarikçi için yerel bölge desteği sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası sağlayıcı, yerel ayar yapmak için bu arabirimi uygulamaya almaktadır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda **IDebugPortSupplierLocale2 yöntemlerini gösterir.**

|Yöntem|Açıklama|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Bağlantı noktası sağlayıcı için yerel ayar ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Portpriv.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
