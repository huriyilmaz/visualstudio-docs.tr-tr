---
title: IDebugPortEvents2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725180"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Bu arabirim, belirli bir bağlantı noktasında işlem ve program oluşturma ve imha dinleyici (genellikle oturum hata ayıklama yöneticisi [SDM] veya hata ayıklama altyapısı) bildirin. Bu bilgiler, bağlantı noktasında çalışan işlemlerin ve programların gerçek zamanlı görünümünü sunmak için kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio genellikle program oluşturma ve imha hakkında bildirimler almak için bu arabirimi uygular. Hata ayıklama altyapısı da bu tür bağlantı noktası olaylarını dinlemek için bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Tüm [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimleri bir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> arabirim için sorgulanabilir. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> Daha sonra `IDebugPortEvents2` bir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> arayüz almak için arabirimde yöntem denir. Son olarak, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> arabirimdeki yöntem [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md) yöntemi ile olayları göndermek için çağrılır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPortEvents2`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Bağlantı noktasındaki işlemlerin ve programların oluşturulmasını ve yok edilmesini açıklayan olaylar gönderir.|

## <a name="remarks"></a>Açıklamalar
 `IDebugPortEvents2`sdm tarafından zaten hata ayıklamakta olan bir işlemde çalışan programları ayıklamak için de kullanılır.

 Bağlantı noktası olayları bu arabirim tarafından SDM'ye aktarılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
