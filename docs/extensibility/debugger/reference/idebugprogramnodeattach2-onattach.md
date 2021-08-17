---
description: İlişkili programa iliştirer veya attach işlemini Attach yöntemine karşılar.
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0650005ca04b01265f6e675db9426856389235caadfc36bb457280d7fbba1fb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402642"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
İlişkili programa iliştirer veya attach işlemini [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine karşılar.

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
 Başarılı olursa `S_OK` döndürür. `S_FALSE` [Attach yönteminin](../../../extensibility/debugger/reference/idebugengine2-attach.md) çağrılmaysa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, Attach yöntemi çağrılmadan [önce, ekleme işlemi](../../../extensibility/debugger/reference/idebugengine2-attach.md) sırasında çağrılır. yöntemi, ekleme işleminin kendisini gerçekleştirebilirsiniz (bu durumda bu yöntem döndürür) veya ekleme işlemini yöntemine `OnAttach` `S_FALSE` `IDebugEngine2::Attach` erteler `OnAttach` (yöntem `S_OK` döndürür). Her iki durumda `OnAttach` da yöntemi, hata `GUID` ayıklaması yapılan programın 'ı verilen olarak `GUID` ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
