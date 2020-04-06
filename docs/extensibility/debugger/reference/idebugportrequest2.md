---
title: IDebugPortRequest2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724791"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Bu arabirim bir bağlantı noktasını açıklar. Bu açıklama, bağlantı noktası tedarikçisine eklemek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio genellikle bir bağlantı noktası tedarikçisinden hata ayıklama bağlantı noktası alma sürecinde bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, hata ayıklama bağlantı noktası oluşturmak için [AddPort'a](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aktarılır. [GetPortRequest'a](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) yapılan bir çağrı, bağlantı noktasını oluşturmak için kullanılan isteği temsil eden bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPortRequest2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Oluşturmak için bağlantı noktasının adını alır.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı genellikle bir bağlantı noktası tedarikçisi ile etkileşime girmez ve bu arabirim için hiçbir kullanımı olmayacaktır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
