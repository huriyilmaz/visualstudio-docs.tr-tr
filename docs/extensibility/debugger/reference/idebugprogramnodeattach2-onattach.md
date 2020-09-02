---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721881"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
İlişkili programa ekler veya Attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.

## <a name="syntax"></a>Söz dizimi

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
