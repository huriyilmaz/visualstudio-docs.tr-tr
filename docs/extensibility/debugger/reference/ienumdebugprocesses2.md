---
title: IEnumDebugProcesses2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715755"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Bu arabirim, hata ayıklama bağlantı noktasında çalışan işlemleri ayıklar.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası tedarikçisi, bağlantı noktasında çalışan işlemlerin listesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arabirimi elde etmek için [EnumProcesses'i](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) arar.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugProcesses2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Numaralandırma sırasında belirli sayıda işlem alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Numaralandırma sırasında belirli sayıda işlemi atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Bir numaralandırmadaki işlem sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual **Studio, Süreçler** penceresini doldurmak için bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
