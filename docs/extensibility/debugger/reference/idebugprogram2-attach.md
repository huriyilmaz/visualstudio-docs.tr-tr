---
description: Programa iliştirir.
title: 'IDebugProgram2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f9565ea0975e38ced80f0747560cf1a24b4150c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076231"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Programa iliştirir.

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
