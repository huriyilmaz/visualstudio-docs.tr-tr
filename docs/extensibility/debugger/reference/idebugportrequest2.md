---
description: Bu arabirim bir bağlantı noktasını tanımlar.
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ca2d1d59c66c87c2dbb0fc256481d35ad590dbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142629"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Bu arabirim bir bağlantı noktasını tanımlar. Bu açıklama, bağlantı noktasını bir bağlantı noktası sağlayıcısına eklemek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, genellikle bir bağlantı noktası tedarikçiden bir hata ayıklama bağlantı noktası alma sürecinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, hata ayıklama bağlantı noktası oluşturmak için [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 'a geçirilir. [Getportrequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) çağrısı, ilk yerde bağlantı noktasını oluşturmak için kullanılan isteği temsil eden bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugPortRequest2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Oluşturulacak bağlantı noktasının adını alır.|

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısı genellikle bir bağlantı noktası sağlayıcısıyla etkileşime girmiyor ve bu arabirim için hiçbir kullanımı olmayacaktır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
