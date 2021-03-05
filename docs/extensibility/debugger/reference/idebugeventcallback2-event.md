---
description: Hata ayıklama olaylarının bildirimini gönderir.
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa0cfd8f96d21a510370a4fc526a3cae053c77b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152929"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Hata ayıklama olaylarının bildirimini gönderir.

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
'ndaki Bu olayı gönderen hata ayıklama altyapısını (DE) temsil eden bir [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) nesnesi. Bu parametreyi doldurması için DE gereklidir.

`pProcess`\
'ndaki Olayın gerçekleştiği işlemi temsil eden bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesi. Bu parametre, oturum hata ayıklama Yöneticisi (SDM) tarafından doldurulur. Bir DE Bu parametre için her zaman null bir değer geçirir.

`pProgram`\
'ndaki Bu olayın gerçekleştiği programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi. Çoğu olay için bu parametre null değer değildir.

`pThread`\
'ndaki Bu olayın gerçekleştiği iş parçacığını temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi. Olayları durdurma için bu parametre, yığın çerçevesi bu parametreden elde edilen bir null değer olamaz.

`pEvent`\
'ndaki Hata ayıklama olayını temsil eden bir [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) nesnesi.

`riidEvent`\
'ndaki Parametresinden hangi olay arabiriminin alınacağını tanımlayan GUID `pEvent` .

`dwAttrib`\
'ndaki [EventAttributes](../../../extensibility/debugger/reference/eventattributes.md) numaralandırmasındaki bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi çağırırken `dwAttrib` parametresi, parametresi içinde geçirilen olay nesnesi üzerinde çağrılan şekilde [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) yönteminden döndürülen değerle eşleşmelidir `pEvent` .

 Tüm hata ayıklama olayları, bir olayın zaman uyumsuz olup olmamasına bakılmaksızın zaman uyumsuz olarak gönderilir. Bu yöntemi çağırdığında, dönüş değeri olayın işlenip işlenmeyeceğini, yalnızca olayın alınıp alınmayacağını göstermez. Aslında, çoğu durumda, bu yöntem döndüğünde olay işlenmemiştir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
