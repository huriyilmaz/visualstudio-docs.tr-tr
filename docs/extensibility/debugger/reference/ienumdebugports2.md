---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 638b17490ba875f8ecab7bf6dcdff7fef161b66e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967806"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Bu arabirim bir makinenin veya bağlantı noktası tedarikçinin bağlantı noktalarını sıralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, tedarikçi tarafından oluşturulan bağlantı noktalarının listesini göstermek için bu arabirimi uygular. Visual Studio bu arabirimi kendi bağlantı noktası tedarikçisine yönelik desteğe uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bağlantı noktası sağlayıcısı tarafından oluşturulan bağlantı noktası listesini temsil eden bu arabirimi almak için, [TRTs](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 'yi çağırın. Diske kaydedilen bağlantı noktalarının listesini temsil eden bu arabirimi almak için [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugPorts2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantı noktasını alır.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda bağlantı noktasını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[Oluşturulacak](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Bir Numaralandırıcı içindeki bağlantı noktası sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio, işlemlere ekleme için kullanılan bağlantı noktası listesinin doldurulmaya yardımcı olmak için bu arabirimi kullanır.

 Bir hata ayıklama altyapısı genellikle bu arabirimi kullanmaz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
