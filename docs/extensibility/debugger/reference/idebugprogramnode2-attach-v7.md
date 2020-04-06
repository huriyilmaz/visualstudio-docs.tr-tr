---
title: IDebugProgramNode2::Attach_V7 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722131"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Kaldırıl -mış. KULLANMAYıN.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parametreler

`pMDMProgram`\
[içinde] Eklenecek programı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimi.

`pCallback`\
[içinde] Hata ayıklama olaylarını SDM'ye göndermek için kullanılacak [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi.

`dwReason`\
[içinde] [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) numaralandırmanın bir değeri, ekleme nedenini belirtir.

## <a name="return-value"></a>Dönüş Değeri

Bir uygulama her `E_NOTIMPL`zaman dönmelidir.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> Visual Studio 2005 itibariyle, bu yöntem artık kullanılmaz ve her zaman geri dönmelidir. `E_NOTIMPL` Program düğümüne bağlanamayacağını belirtmek için gerekirse veya program düğümü yalnızca programı `GUID`ayarlıyorsa, alternatif bir yaklaşım için [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimine bakın. Aksi takdirde, [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemini uygulayın.

## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005'e kadar

Bu yöntemin yalnızca DE, debugged olan programın adres alanında çalışıyorsa uygulanması gerekir. Aksi takdirde, bu `S_FALSE`yöntem in verilmelidir.

Bu yöntem çağrıldığında, DE [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesini göndermeli, [iDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) arabiriminin bu örneğinin yanı sıra [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ve [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesneleri için gönderilmemişse. `dwReason` `ATTACH_REASON_LAUNCH` [Parametre](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .

DE, `IDebugProgram2` [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogram2.md) olay nesnesi tarafından sağlanan [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) nesnesi üzerinde [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini aramalı ve bu programın GUID'ini DE tarafından uygulanan nesnenin örnek verilerinde depolamalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
