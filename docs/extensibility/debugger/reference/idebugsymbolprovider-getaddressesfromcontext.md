---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719438"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Bu yöntem, belge bağlamını hata ayıklama adresleri dizisine eşler.

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
[içinde] Belge bağlamı.

`fStatmentOnly`\
[içinde] TRUE ise, hata ayıklama adreslerini tek bir ifadeyle sınırlar.

`ppEnumBegAddresses`\
[çıkış] Bu deyim veya satırla ilişkili başlangıç hata ayıklama adresleri için bir sayısalatör döndürür.

`ppEnumEndAddresses`\
[çıkış] Bu deyim veya satırla ilişkili son hata ayıklama adresleri için bir [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) kayıt dışı verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belge bağlamı genellikle bir dizi kaynak satırı gösterir. Bu yöntem, bu satırlarla ilişkili başlangıç ve bitiş hata ayıklama adreslerini sağlar. Bazı diller, birden çok satırı veya birden fazla deyim içeren satırları kapsayan ifadelere izin verir. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.

 Şablonlarda olduğu gibi tek bir ifadenin birden çok hata gideri adresi olması mümkündür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
