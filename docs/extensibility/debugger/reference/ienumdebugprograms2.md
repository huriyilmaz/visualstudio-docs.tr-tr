---
title: IEnumDebugPrograms2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715577"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Bu arabirim, geçerli hata ayıklama oturumunda çalışan programları ayıklar.

## <a name="syntax"></a>Sözdizimi

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), DE tarafından debugged olan programların bir listesini sağlamak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Visual Studio bu arabirimi elde etmek için [EnumPrograms'ı](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) arar. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) Visual Studio tarafından kullanılmaz.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IEnumDebugPrograms2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Numaralandırma sırasında belirli sayıda program alır.|
|[Atlamak](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Numaralandırma sırasında belirli sayıda programı atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Numaralandırma sırasını başa sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Geçerli numaralandırma durumuyla aynı numaralandırma durumunu içeren bir numaralandırma oluşturucu oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Bir numaralandırmadaki program sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio bu arabirimi şu şekilde kullanır:

- **Modüller** penceresini doldurma [(EnumPrograms'ı](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) çağırarak ve her programda [EnumModules'i](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) arayarak).

- **İşleme Ekle** listesini doldurma `IDebugProcess2::EnumPrograms` [(IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) arabirimi elde etmek için her [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde [QueryInterface'i](/cpp/atl/queryinterface) arayarak ve ardından çağırarak).

- İşlemdeki her programı hata ayıklayabilen [(GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)kullanarak) DEs listesi oluşturun.

- Her programa Düzenleme ve Devam (ENC) güncelleştirmelerini uygulayın (IDebugProcess2::EnumPrograms'ı ve ardından [GetENCUpdate'i](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)arayarak).

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
