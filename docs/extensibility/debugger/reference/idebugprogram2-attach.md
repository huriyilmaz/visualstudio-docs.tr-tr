---
title: IDebugProgram2::Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723141"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Programa bağlanır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parametreler
`pCallback`\
[içinde] Hata ayıklama olay bildirimi için kullanılacak bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bazı olası hata kodları gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Belirtilen program hata ayıklama zaten bağlı.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ekleme işlemi sırasında bir güvenlik ihlali oluştu.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Bir masaüstü programı hata ayıklama eklenemez.|

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama altyapısı (DE) hiçbir zaman bu yöntemi bir programa eklemek için aramaz. Programın adres alanında DE çalışıyorsa, [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi çağrılır. De oturum hata ayıklama yöneticisinin (SDM) adres alanında çalışıyorsa, [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
