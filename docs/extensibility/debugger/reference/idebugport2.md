---
title: IDebugPort2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725237"
---
# <a name="idebugport2"></a>IDebugPort2
Bu arabirim, makinedeki hata ayıklama bağlantı noktasını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, makinedeki hata ayıklama bağlantı noktasını temsil etmek için bu arabirimi uygular.

 Bağlantı noktası, bağlantı noktası olaylarını göndermeyi <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> destekliyorsa, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [iDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) arabirimini sağlayan bir arabirimi desteklemek için arabirimi de uygulaması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) veya [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağrıları, istenen bağlantı noktasını temsil eden bu arabirimi döndürer.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugPort2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Bağlantı noktası adını döndürür.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Bağlantı noktası tanımlayıcısını döndürür.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Bağlantı noktası oluşturmak için kullanılan isteği döndürür (varsa).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Bu bağlantı noktası nın bağlantı noktası tedarikçisini döndürür.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|İşlemin tanımlayıcısı verilen işleme bir arabirim döndürür.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Bir bağlantı noktasında çalışan tüm işlemleri oyalar.|

## <a name="remarks"></a>Açıklamalar
 Yerel bağlantı noktası, yerel makinede çalışan tüm işlemlere ve programlara erişim sağlar. Diğer bağlantı noktaları, Windows CE tabanlı bir aygıta seri kablo bağlantısını veya DCOM olmayan bir bilgisayara ağ bağlantısını temsil edebilir. Arabirim, `IDebugPort2` bir bağlantı noktasının adını ve tanımlayıcısını bulmak ve bağlantı noktasında çalışan tüm işlemleri saymak için kullanılır. Bağlantı noktasındaki süreçleri başlatma ve sonlandırma tesisleri `IDebugPortEx2` arayüz içinde uygulanmaktadır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
