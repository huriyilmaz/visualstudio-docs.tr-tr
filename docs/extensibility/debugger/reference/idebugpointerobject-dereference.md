---
title: IDebugPointerObject::Dereference | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725571"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Nesneyi işaret ediyor.

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
[içinde] Işaret nesnenin başından itibaren basit bir bayt ofset.

`ppObject`\
[çıkış] Işaret edilen nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi ve varsa ofset döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür. Bu nesne başka bir nesneyi işaret etmiyorsa E_FAIL döndürür.

## <a name="remarks"></a>Açıklamalar
 Işaret edilen nesne, bir sınıf veya yapı gibi ilkel veya daha karmaşık bir tür olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
