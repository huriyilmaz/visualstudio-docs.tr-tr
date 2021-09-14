---
description: Bu arabirim, ağdaki bir makinedeki bir sunucudan bilgi göstermek ve almak için kullanılır.
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ebee42f829a3824477fa5c5e84870ad9a16462bf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725249"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Bu arabirim, ağdaki bir makinedeki bir sunucudan bilgi göstermek ve almak için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Visual Studio, bu arabirimi bir sunucuyu temsil etmek için uygular. her Visual Studio örneği bu arabirimin bir örneğini oluşturur.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Özel bir bağlantı noktası sağlayıcısı bu arabirimi bir [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)çağrısıyla alır.

 Bir hata ayıklama altyapısı, bu arabirimi bir [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) çağrısıyla dolaylı olarak alabilir ( [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), öğesinden türetilmiş bir arabirim `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCoreServer2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Bir makinenin adını ve özniteliklerini alır.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Makinenin adını alır.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Bir makinede bulunan bir bağlantı noktası sağlayıcısı alır.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Bir makinede zaten bulunan bir bağlantı noktasını alır.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Bir makinedeki tüm bağlantı noktaları için bir Numaralandırıcı oluşturur.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Bir makinedeki tüm bağlantı noktası tedarikçileri için bir Numaralandırıcı oluşturur.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Makine için makine yardımcı programlarını alır.|

## <a name="remarks"></a>Açıklamalar
 bu arabirim, ağdaki makinelerde çalışan işlemlere gitmek için Visual Studio tarafından da kullanılır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
