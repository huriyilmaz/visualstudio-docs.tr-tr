---
description: Bu yöntem, bir belge bağlamını bir hata ayıklama adresleri dizisine eşler.
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02f0ef70eed558b0a0aca35544f9000de6ef739a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126108"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Bu yöntem, bir belge bağlamını bir hata ayıklama adresleri dizisine eşler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametreler
`pDocContext`\
[in] Belge bağlamı.

`fStatmentOnly`\
[in] TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlar.

`ppEnumBegAddresses`\
[out] Bu deyim veya satırla ilişkili başlangıç hata ayıklama adresleri için bir numaralayıcı döndürür.

`ppEnumEndAddresses`\
[out] Bu deyim veya satırla ilişkili son hata ayıklama adresleri için [bir IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) numaralayıcı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belge bağlamı genellikle bir kaynak satırı aralığını gösterir. Bu yöntem, bu satırlarla ilişkili başlangıç ve bitiş hata ayıklama adreslerini sağlar. Bazı diller birden çok satıra yayılan deyimlere veya birden fazla deyim içeren satırlara izin veriyor. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.

 Şablonlarda olduğu gibi tek bir deyimin birden çok hata ayıklama adresine sahip olmak mümkündür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
