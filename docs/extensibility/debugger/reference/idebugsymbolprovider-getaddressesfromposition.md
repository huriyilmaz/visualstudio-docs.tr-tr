---
description: Bu yöntem, bir belge konumunu bir hata ayıklama adresleri dizisine eşler.
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ea5d2bbfdec859b82ffbe49adff18d0d60b8cc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095901"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Bu yöntem, bir belge konumunu bir hata ayıklama adresleri dizisine eşler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametreler
`pDocPos`\
[in] Belge konumu.

`fStatmentOnly`\
[in] TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlar.

`ppEnumBegAddresses`\
[out] Bu deyim veya satırla ilişkili başlangıç hata ayıklama adresleri için bir numaralayıcı döndürür.

`ppEnumEndAddresses`\
[out] Bu deyim veya satırla ilişkili son hata ayıklama adresleri için [bir IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) numaralayıcı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belge konumu genellikle bir kaynak satır aralığını gösterir. Bu yöntem, bu satırlarla ilişkili başlangıç ve bitiş hata ayıklama adreslerini sağlar. Bazı diller birden çok satıra yayılan deyimlere veya birden fazla deyim içeren satırlara izin veriyor. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.

 Şablonlarda olduğu gibi tek bir deyimin birden çok hata ayıklama adresine sahip olmak mümkündür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
