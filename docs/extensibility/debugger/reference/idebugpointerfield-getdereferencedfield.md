---
title: IDebugPointerField::GetDereferencedField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 617711a611e6eb1ea162c3abd8ad2b793b4756cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725615"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Bu yöntem, bu işaretçi nesnesinin işaret ettiği nesne türünü döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametreler
`ppField`\
[çıkış] Hedef nesne türünü açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) nesnesi bir tamsayıya işaret ederse, bu yöntemle döndürülen [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) türü bu tamsayı türünü açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
