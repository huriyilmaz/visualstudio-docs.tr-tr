---
description: Bir bağlantı noktası sağlayıcısı için bir çekirdek sunucu seçmek ve bunlarla etkileşim kurmak için destek sağlar.
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fc8909ac858bbc35fc39ea8c850729d83d9b14cb6152fa397ec37015d100b830
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416500"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Bir bağlantı noktası sağlayıcısı için bir çekirdek sunucu seçmek ve bunlarla etkileşim kurmak için destek sağlar.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı bu arabirimi, kullanılacak çekirdek sunucuyu seçebilmeniz için uygular.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda **IDebugPortSupplierEx2** yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Bağlantı noktası sağlayıcısı için çekirdek sunucuyu ayarlar.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
