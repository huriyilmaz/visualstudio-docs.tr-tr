---
description: İşaret eden nesneyi alır.
title: Ihata ayıklama Gpoınterobject::D ereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226e8471d83208e9647578fca0fa16cc7b49e4eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087645"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
İşaret eden nesneyi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`dwIndex`\
'ndaki Nesnenin başlangıcından başlayan basit bir bayt kayması.

`ppObject`\
dışı İşaret edilen nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi ve varsa, bu nesneyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür. Bu nesne başka bir nesneye işaret içermiyorsa E_FAIL döndürür.

## <a name="remarks"></a>Açıklamalar
 İşaret eden nesne, temel veya sınıf ya da yapı gibi daha karmaşık bir tür olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
