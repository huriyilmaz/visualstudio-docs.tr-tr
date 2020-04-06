---
title: IEnumDebugPorts2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716109"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Bu arabirim, bir makine veya bağlantı noktası tedarikçisinin bağlantı noktalarını içerir.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, tedarikçi tarafından oluşturulan bağlantı noktalarının listesini temsil etmek için bu arabirimi uygular. Visual Studio kendi bağlantı noktası tedarikçisi desteklemek için bu arayüzü uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bağlantı noktası tedarikçisi tarafından oluşturulan bağlantı noktalarının listesini temsil eden bu arabirimi elde etmek için [EnumPorts'u](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) arayın. Diske kaydedilmiş bağlantı noktalarının listesini temsil eden bu arabirimi elde etmek için [EnumPersistedPorts'u](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugPorts2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Numaralandırma sırasında belirtilen sayıda bağlantı noktası nı alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Numaralandırma sırasında belirli sayıda bağlantı noktası atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Bir numaralandırmadaki bağlantı noktası sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, işlemlere iliştirmek için kullanılan bağlantı noktalarının listesini doldurmaya yardımcı olmak için bu arabirimi kullanır.

 Hata ayıklama altyapısı genellikle bu arabirimi kullanmaz.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
