---
title: 'IDebugSymbolProvider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15838ff1efe9cba6920b98a8b7f00cb62f2fc3b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956470"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Bu yöntem bir belge konumunu hata ayıklama adresleri dizisiyle eşler.

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
'ndaki Belge konumu.

`fStatmentOnly`\
'ndaki TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlandırır.

`ppEnumBegAddresses`\
dışı Bu deyimle veya satırla ilişkili başlangıç hata ayıklama adresleri için bir Numaralandırıcı döndürür.

`ppEnumEndAddresses`\
dışı Bu deyimle veya satırla ilişkili bitiş hata ayıklama adresleri için bir [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) numaralandırıcısı döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belge konumu genellikle kaynak satır aralığını gösterir. Bu yöntem, bu satırlarla ilişkili hata ayıklama adreslerini başlatma ve sonlandırma sağlar. Bazı diller birden çok satırı kapsayan deyimlere veya birden fazla deyim içeren satırlara izin verir. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.

 Tek bir deyimin, şablonlar söz konusu olduğunda olduğu gibi birden çok hata ayıklama adresi olması mümkündür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
