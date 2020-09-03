---
title: 'IDebugProgram2:: Attach | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723141"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Programa iliştirir.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Hata ayıklama olayı bildiriminde kullanılacak bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda bazı olası hata kodları gösterilmektedir.

|Değer|Açıklama|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Belirtilen program hata ayıklayıcıya zaten eklenmiş.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|İliştirme yordamı sırasında bir güvenlik ihlali oluştu.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Bir masaüstü programı hata ayıklayıcıya eklenemiyor.|

## <a name="remarks"></a>Açıklamalar
 Bir hata ayıklama altyapısı (DE) bir programa eklemek için hiçbir şekilde bu yöntemi çağırmazlar. DE programın adres alanında çalışıyorsa [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemi çağırılır. DE, oturum hata ayıklama yöneticisinin (SDM) adres alanında çalıştırılıyorsa, [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi çağırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
