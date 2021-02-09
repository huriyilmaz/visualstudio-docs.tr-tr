---
title: 'Ihata ayıklama Gpoınterfield:: Getbaşvurunun Encedfield | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b502b83ec793733ef642585b6ded260f72aa1be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869667"
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
dışı Hedef nesnenin türünü açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, [ıdebuggpoınterfield](../../../extensibility/debugger/reference/idebugpointerfield.md) nesnesi bir tamsayıya işaret ediyorsa, bu yöntem tarafından döndürülen [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) türü bu tamsayı türünü açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
