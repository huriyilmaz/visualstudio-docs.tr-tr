---
description: Bir özelliğin türetilen en çok özelliğini alır.
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afa85a74a5104725f6712667317f8a5b8acfff0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132580"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Bir özelliğin türetilen en çok özelliğini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametreler
`ppDerivedMost`\
dışı En çok türetilen özelliği temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür. `S_GETDERIVEDMOST_NO_DERIVED_MOST`Alınacak türetilmiş bir özellik yoksa, döndürür.

## <a name="remarks"></a>Açıklamalar
 Örneğin, bu özellik, `ClassRoot` tarafından türetilen ancak gerçekten bir örnek oluşturma olan bir nesne tanımlıyor `ClassDerived` `ClassRoot` , bu yöntem, nesneyi açıklayan bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür `ClassDerived` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
