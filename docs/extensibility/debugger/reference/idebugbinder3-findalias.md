---
title: IDebugBinder3::FindAlias | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735866"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Bu yöntem, bir ad verilen bir diğer adı bulur. Bu, programdaki tüm diğer adları arar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`pcstrName`\
[içinde] Bulmak için takma adı.

`ppAlias`\
[çıkış] [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) arabirimi tarafından temsil edilen diğer ad (varsa) bulundu.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, (takma ad bulunamazsa) veya bir hata kodu döndürür. `S_FALSE`

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, aramadan önce hedef nesneyi null olarak adlandırır; daha sonra diğer adın bulunup bulunmadığını belirlemek için null değeri için test olur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
