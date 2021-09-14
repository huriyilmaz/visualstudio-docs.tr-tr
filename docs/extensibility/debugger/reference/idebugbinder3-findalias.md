---
description: Bu yöntem, verilen adla bir diğer ad kullanır.
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8138d702fb8507cfb1da24f28995b2bc4d21341f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627494"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Bu yöntem, verilen adla bir diğer ad kullanır. Bu, programda tüm diğer adları aratır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`pcstrName`\
[in] Bulunan diğer adın adı.

`ppAlias`\
[out] [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) arabirimi tarafından temsil edilen diğer ad bulundu (varsa).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde `S_FALSE` döndürür (diğer ad bulunamıyorsa) veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, çağrılmadan önce hedef nesneyi null olarak başlatıyor; daha sonra diğer adın bulunıp buluna olmadığını belirlemek için null değeri test etti.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
