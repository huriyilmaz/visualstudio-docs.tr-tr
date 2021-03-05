---
description: Bu yöntem, bir bağlantı noktasındaki işlemlerin ve programların oluşturulmasını ve yok edilmesiyle ilgili olayları gönderir.
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc975c2f48c560d0f15f08a6cc957c67ecc13808
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142914"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Bu yöntem, bir bağlantı noktasındaki işlemlerin ve programların oluşturulmasını ve yok edilmesiyle ilgili olayları gönderir.

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
'ndaki Olayın gerçekleştiği hata ayıklama sunucusunu (her örneği için bir tane) temsil eden bir [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) nesnesi [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

`pPort`\
'ndaki Olayın gerçekleştiği bağlantı noktasını temsil eden bir [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) nesnesi.

`pProcess`\
'ndaki Olayın gerçekleştiği işlemi temsil eden bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesi.

`pProgram`\
'ndaki Olayın gerçekleştiği programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`pEvent`\
'ndaki Olayı tanımlayan bir [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) nesnesi. Olası olaylar aşağıdaki gibidir:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
'ndaki Etkinliğin GUID 'SI. Bu yöntem çağrılmadan önce olay [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) olarak yayınlandığından, bu tanımlayıcı hangi olayın gönderildiğini belirlemeyi kolaylaştırır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
