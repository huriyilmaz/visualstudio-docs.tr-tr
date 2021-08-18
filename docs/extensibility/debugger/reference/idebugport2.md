---
description: Bu arabirim, bir makinede hata ayıklama bağlantı noktasını temsil eder.
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ca97bd3a89358f374e66a1c35693ca4f2801641c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133022"
---
# <a name="idebugport2"></a>IDebugPort2
Bu arabirim, bir makinede hata ayıklama bağlantı noktasını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası sağlayıcı, makinede hata ayıklama bağlantı noktasını temsil etmek için bu arabirimi uygulamaya almaktadır.

 Bağlantı noktası bağlantı noktası olaylarını göndermeyi destekliyorsa, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini sağlayan bir arabirimi desteklemek için arabirimini de uygulaması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetPort veya](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) [AddPort çağrıları,](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) istenen bağlantı noktasını temsil eden bu arabirimi geri döner.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugPort2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Bağlantı noktası adını döndürür.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Bağlantı noktası tanımlayıcısını döndürür.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Bağlantı noktası oluşturmak için kullanılan isteği döndürür (varsa).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Bu bağlantı noktası için bağlantı noktası sağlayıcıyı döndürür.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|sürecin tanımlayıcısına göre işleme bir arabirim döndürür.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Bir bağlantı noktası üzerinde çalışan tüm işlemleri numaralar.|

## <a name="remarks"></a>Açıklamalar
 Yerel bağlantı noktası, yerel makinede çalışan tüm işlemlere ve programlara erişim sağlar. Diğer bağlantı noktaları, Windows CE tabanlı bir cihaza seri kablo bağlantısını veya DCOM olmayan bir bilgisayara yapılan ağ bağlantısını temsil ediyor olabilir. Arabirim, bir bağlantı noktasının adını ve tanımlayıcısını bulmak ve bağlantı noktası üzerinde çalışan `IDebugPort2` tüm işlemlerin numarasını bulmak için kullanılır. Bağlantı noktası üzerinde işlemleri başlatma ve sonlandırma özellikleri arabirimde `IDebugPortEx2` uygulanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
