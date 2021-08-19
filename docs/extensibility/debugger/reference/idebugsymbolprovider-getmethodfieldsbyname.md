---
description: Bu yöntem, tam yöntem adını temsil eden alanı alır.
title: IDebugSymbolProvider::GetMethodFieldsByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cd7053f8d4bea283a47d6cce8042c9a303cb8e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063713"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Bu yöntem, tam yöntem adını temsil eden alanı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`pszFullName`\
[in] Yöntem adı.

`nameMatch`\
[in] Eşleşme türünü (örneğin, büyük/büyük/büyük harfe duyarlı) seçer.

`ppEnum`\
[out] Bu yöntemle ilişkili alanlar için bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) numaralayıcı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir yöntem, örneğin aşırı yüklenmişse birden çok alanla ilişkilendirilebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
