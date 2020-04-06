---
title: IDebugDefaultPort2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732321"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Bu arabirim, bir bağlantı noktasının sunucu ve bildirim tesislerine erişmek için çeşitli yöntemler sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio, programlara erişmek için hata ayıklama bağlantı noktasını temsil etmek için bu arabirimi uygular. Özel bir bağlantı noktası tedarikçisi, uzaktan hata ayıklama işliyorsa bu arabirimi de uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimindeki yöntemlere yönelik bir bağımsız değişken bu arabirimi sağlar. Bir [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde [QueryInterface](/cpp/atl/queryinterface) arama da bu arabirimi elde edebilirsiniz.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [IDebugPort2'de](../../../extensibility/debugger/reference/idebugport2.md)tanımlanan yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Bu bağlantı noktasından bağlantı noktası bildirim arabirimini alır.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Arabirimi bu bağlantı noktasını barındıran sunucuya getirir.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bu bağlantı noktasının yerel makinede çalışıp çalışmadığını belirler.|

## <a name="remarks"></a>Açıklamalar
 " "`IDebugDefaultPort2`adı, varsayılan bir bağlantı noktasını temsil etmediğinden, biraz yanlış isimdir. Adı "IDebugPort3" olabilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
