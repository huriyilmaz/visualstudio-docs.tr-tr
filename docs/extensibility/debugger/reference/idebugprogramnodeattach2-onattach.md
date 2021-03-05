---
description: İlişkili programa ekler veya Attach işlemini Attach yöntemine erteler.
title: 'IDebugProgramNodeAttach2:: OnAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d1fdb6f0e2fe41555dbbc3b1bcfd16a1a2b4240
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167054"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
İlişkili programa ekler veya Attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parametreler
`guidProgramId`\
[in] `GUID` ilişkili programa atamak için.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` . `S_FALSE` [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yönteminin çağrılmaması gerekiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, [Attach yöntemi çağrılmadan önce iliştirme işlemi](../../../extensibility/debugger/reference/idebugengine2-attach.md) sırasında çağrılır. `OnAttach`Yöntemi, Attach işlemini kendisi gerçekleştirebilir (Bu durumda, bu yöntem ' i döndürür `S_FALSE` ) veya iliştirme işlemini yönteme erteleyin `IDebugEngine2::Attach` ( `OnAttach` Yöntem döndürür `S_OK` ). Her iki olayda da `OnAttach` yöntemi, `GUID` hata ayıklanan programın belirtilen ' a göre ayarlayabilir `GUID` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
