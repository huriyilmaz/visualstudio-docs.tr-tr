---
title: IDebugCoreServer2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733026"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Bu arabirim, ağdaki bir makinedeki bir sunucuyu temsil etmek ve bunlardan bilgi almak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio bir sunucutemsil etmek için bu arabirimi uygular. Visual Studio'nun her örneği bu arabirimin bir örneğini oluşturur.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Özel bir bağlantı noktası tedarikçisi bu arabirimi [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)çağrısında alır.

 Hata ayıklama altyapısı bu arabirimi [getserver'a](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) yapılan bir çağrı yla dolaylı olarak elde edebilir `IDebugCoreServer2`(bu arabirim Den türetilen bir arabirim olan [IDebugCoreServer3'ü](../../../extensibility/debugger/reference/idebugcoreserver3.md)döndürür).

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugCoreServer2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Bir makinenin adını ve özniteliklerini alır.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Bir makinenin adını alır.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Bir makinede bulunan bir bağlantı noktası tedarikçisi alır.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Zaten bir makinede var olan bir bağlantı noktası alır.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Makinedeki tüm bağlantı noktaları için bir sayısallaştırıcı oluşturur.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Bir makinedeki tüm liman tedarikçileri için bir sayısallaştırıcı oluşturur.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Bir makine için makine yardımcı programları alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, Visual Studio tarafından ağdaki makinelerde çalışan işlemlere göz atmak için de kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
