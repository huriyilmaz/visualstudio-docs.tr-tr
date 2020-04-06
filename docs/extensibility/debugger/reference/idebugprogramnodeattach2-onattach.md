---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721881"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
İlişkili programa bağlanır veya ekleme işlemini [Ekle](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemine erteler.

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
[içinde] `GUID` ilişkili programa atamak için.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döndürür. Ekle `S_FALSE` yöntemi [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) çağrılmaması gerekiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, ekleme işlemi sırasında, [Ekleme](../../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi çağrılmadan önce çağrılır. Yöntem `OnAttach` ekleme işleminin kendisini gerçekleştirebilir (bu durumda, bu yöntem `S_FALSE`döndürür) veya ekleme işlemini `IDebugEngine2::Attach` yönteme erteleyebilir `OnAttach` (yöntem döndürür). `S_OK` Her iki durumda `OnAttach` da, `GUID` yöntem verilen debugged olan `GUID`programın ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [İliştir](../../../extensibility/debugger/reference/idebugengine2-attach.md)
