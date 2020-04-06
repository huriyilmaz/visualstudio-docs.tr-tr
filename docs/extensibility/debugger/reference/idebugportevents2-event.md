---
title: IDebugPortEvents2::Olay | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725240"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Bu yöntem, bir bağlantı noktasında ki işlemlerin ve programların oluşturulması nı ve yok edilmesini ifade eden olaylar gönderir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parametreler
`pMachine`\
[içinde] Hata ayıklama sunucusunu temsil eden bir [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) nesnesi (olayın meydana geldiği her örneği için bir tane [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]vardır).

`pPort`\
[içinde] Olayın oluştuğu bağlantı noktasını temsil eden bir [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi.

`pProcess`\
[içinde] Olayın oluştuğu işlemi temsil eden bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesi.

`pProgram`\
[içinde] Olayın oluştuğu programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`pEvent`\
[içinde] Olayı tanımlayan bir [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) nesnesi. Olası olaylar aşağıdaki gibidir:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[içinde] Olayın GUID. Olay bu yöntemi aramadan önce [IDebugEvent2'ye](../../../extensibility/debugger/reference/idebugevent2.md) ait olduğundan, bu tanımlayıcı hangi olayın gönderildiğini belirlemeyi kolaylaştırır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
