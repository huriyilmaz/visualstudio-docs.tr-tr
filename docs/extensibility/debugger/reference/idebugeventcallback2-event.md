---
title: IDebugEventCallback2::Olay | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729901"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Hata ayıklama olayları bildirimi gönderir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Parametreler
`pEngine`\
[içinde] Bu olayı gönderen hata ayıklama altyapısını (DE) temsil eden bir [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) nesnesi. Bu parametreyi doldurmak için DE gereklidir.

`pProcess`\
[içinde] Olayın oluştuğu işlemi temsil eden bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesi. Bu parametre oturum hata ayıklama yöneticisi (SDM) tarafından doldurulur. De her zaman bu parametre için null değeri geçer.

`pProgram`\
[içinde] Bu olayın gerçekleştiği programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi. Çoğu olay için bu parametre null değeri değildir.

`pThread`\
[içinde] Bu olayın oluştuğu iş parçacığı temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi. Olayları durdurmak için, yığın çerçevesi bu parametreden elde edildiklerinden bu parametre null değer olamaz.

`pEvent`\
[içinde] Hata ayıklama olayını temsil eden bir [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) nesnesi.

`riidEvent`\
[içinde] `pEvent` Parametreden hangi olay arabiriminin alınabilmek için guid.

`dwAttrib`\
[içinde] [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) numaralandırmagelen bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi ararken, `dwAttrib` parametre, `pEvent` parametrede geçen olay nesnesinde çağrıldığı gibi [GetÖzler](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) yönteminden döndürülen değeri eşleştirmelidir.

 Tüm hata ayıklama olayları, bir olayın kendisinin eşzamanlı olup olmadığına bakılmaksızın eşitsiz olarak deftere nakledilir. Bir DE bu yöntemi aradığında, iade değeri olayın işlenip işlenmediğini değil, yalnızca olayın alınıp alınmadığını gösterir. Aslında, çoğu durumda, bu yöntem döndüğünde olay işlenmedi.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
